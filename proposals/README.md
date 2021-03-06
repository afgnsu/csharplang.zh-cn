---
ms.openlocfilehash: aa0c233e7739ae7a0a7752251aae6f89df18ba93
ms.sourcegitcommit: 94a3d151c438d34ede1d99de9eb4ebdc07ba4699
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/25/2019
ms.locfileid: "79483510"
---
# <a name="c-language-proposals"></a>C#语言建议

语言建议是活动文档，描述了有关给定语言功能的当前考虑。

建议可以是*活动*、*非活动*、已*拒绝*或已*完成*。 *活动*提议直接存储在 "提议" 文件夹中，*非*活动和已*拒绝*的提议存储在 "[非活动](proposals/inactive)" 和 "已[拒绝](proposals/rejected)" 子文件夹中，并将已*完成*的提议存档到与它们所属的语言版本相对应的文件夹中。

## <a name="lifetime-of-a-proposal"></a>提议的生存期

当语言设计团队确定它可能会在一天内使语言成为一种很好的补充时，就开始了一个提议。 通常情况下，它将开始*处于活动状态*，但如果我们想要捕获一种想法，而不想立即处理，则建议也可以在*非活动*子文件夹中开始。 如果我们想要记录我们不想执行的操作，则可能会直接在 "已*拒绝*" 状态下开始提出建议。 例如，如果无法实现常用和定期请求，我们可以将其作为已拒绝的建议进行捕获。

建议在[讨论问题](https://github.com/dotnet/csharplang/labels/Discussion)中作为一种想法开始，或者从语言设计会议中的讨论开始，或者从许多其他方面获得。 重要的是，设计团队认为应该已经完成了，并且有愿意写它的人。 通常，语言设计团队的成员会将自己分配为受[冠军问题](https://github.com/dotnet/csharplang/labels/Proposal%20champion)跟踪的功能的拥护者。 冠军负责在设计过程中移动方案。

如果提议在设计和实现方向前进到即将发布的版本中，则该建议处于*活动状态*。 *完成此操作*后（即，实现已合并到一个版本，并且已指定该功能）后，它将被移动到与其版本相对应的子目录中。

如果某个功能根本不可能将其设置为语言（例如，因为它证明不可行，则似乎没有添加足够的值，或者不是正确的语言，则会被[拒绝](proposals/rejected)。 如果某个功能具有合理的承诺，但当前未按优先级工作，则可能会将其声明为[非活动状态](proposals/inactive)，以避免主文件夹混乱。 在非活动或拒绝的提议上完成工作是一种完美的工作，并且在以后复活。 类别用于反映当前设计意图。

## <a name="nature-of-a-proposal"></a>提议的性质

建议[模板](proposal-template.md)应遵循建议。 最好的建议：

- 适合语言的一般精神和美观。
- 不会为现有功能引入更细微的替代语法。
- 为一组清晰的用户添加大量值。
- 不会显著增加语言的复杂性，尤其是对于新用户。  

## <a name="discussion-of-proposals"></a>建议的讨论

[讨论问题](https://github.com/dotnet/csharplang/labels/Discussion)中讨论了反馈和讨论。 向建议文件夹中添加新的提议时，应由冠军或建议作者在讨论问题中公布。 

 