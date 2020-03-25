---
ms.openlocfilehash: 25756c1811d5e6dc97512ce70f99ab7fefa91c4a
ms.sourcegitcommit: 2a6dffb60718065ece95df75e1cc7eb509e48a8d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/01/2020
ms.locfileid: "79484128"
---
# <a name="records-work-in-progress"></a>记录正在进行的工作

不同于其他记录建议，这不是一项提议，而是一项工作，用于记录有关记录功能的共识设计决策。 为了解决问题，将根据需要添加规范详细信息。

建议添加记录的语法，如下所示：

```antlr
class_declaration
    : attributes? class_modifiers? 'partial'? 'class' identifier type_parameter_list?
      parameter_list? type_parameter_constraints_clauses? class_body
    ;

struct_declaration
    : attributes? struct_modifiers? 'partial'? 'struct' identifier type_parameter_list?
      parameter_list? struct_interfaces? type_parameter_constraints_clauses? struct_body
    ;

class_body
    : '{' class_member_declarations? '}'
    | ';'
    ;

struct_body
    : '{' struct_members_declarations? '}'
    | ';'
    ;
```

`attributes` 非终端还将允许 `data`的新上下文属性。

用参数列表或 `data` 修饰符声明的类（结构）称为记录类（record struct），其中的任何一个是记录类型。

声明不包含参数列表和 `data` 修饰符的记录类型是错误的。

## <a name="members-of-a-record-type"></a>记录类型的成员

除了在类体中声明的成员以外，记录类型还具有下列附加成员：

### <a name="primary-constructor"></a>主构造函数

记录类型具有公共构造函数，该构造函数的签名对应于类型声明的值参数。 这称为类型的主构造函数，并导致禁止显示隐式声明的默认构造函数。 类中已存在具有相同签名的主构造函数和构造函数是错误的。
在运行时，主构造函数 

1. 执行出现在类体中的实例字段初始值设定项;然后调用不带参数的基类构造函数。

1. 为对应于值参数的属性初始化编译器生成的支持字段（如果这些属性是编译器提供的属性，请参阅[合成属性](#Synthesized Properties)）


[] TODO：添加基本调用语法和有关通过重载决策选择基构造函数的规范

### <a name="properties"></a>属性

对于记录类型声明的每个记录参数，都有一个对应的公共属性成员，其名称和类型取自值参数声明。 如果没有显式声明或继承具有 get 访问器和此名称和类型的具体（即非抽象）属性，则编译器将生成，如下所示：

对于记录结构或记录类：

* 创建一个公共的仅获取自动属性。 在构造过程中，它的值将与相应的主构造函数参数的值一起初始化。 将重写每个 "匹配" 继承抽象属性的 get 访问器。

### <a name="equality-members"></a>相等成员

记录类型为以下方法生成合成实现：

* 除非已密封或用户提供，否则 `object.GetHashCode()` 重写
* 除非已密封或用户提供，否则 `object.Equals(object)` 重写
* `T Equals(T)` 方法，其中 `T` 是当前类型

指定 `T Equals(T)` 以执行值相等性，将与每个主构造函数参数相同的属性与其他类型的相应属性进行比较。
`object.Equals` 执行等效操作

```C#
override Equals(object o) => Equals(o as T);
```