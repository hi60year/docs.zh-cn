---
title: 类型提升
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- Partial keyword [Visual Basic], unexpected results with type promotion
- scope [Visual Basic], declared elements
- scope [Visual Basic], Visual Basic
- type promotion
- declared elements [Visual Basic], visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
ms.openlocfilehash: aa05bd7dc87510aedb0facadf4b7590c8ec57d1f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345272"
---
# <a name="type-promotion-visual-basic"></a>类型提升 (Visual Basic)
在模块中声明编程元素时 Visual Basic 会将其范围提升到包含该模块的命名空间。 这称为*类型提升*。  
  
 下面的示例演示模块的主干定义以及该模块的两个成员。  
  
 [!code-vb[VbVbalrDeclaredElements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#1)]  
  
 在 `projModule`中，在模块级别声明的编程元素将提升为 `projNamespace`。 在前面的示例中，`basicEnum` 和 `innerClass` 会升级，但 `numberSub` 不是，因为它未在模块级别声明。  
  
## <a name="effect-of-type-promotion"></a>类型提升的效果  
 类型提升的影响在于，限定字符串不需要包含模块名称。 下面的示例对上述示例中的过程进行了两次调用。  
  
 [!code-vb[VbVbalrDeclaredElements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#2)]  
  
 在前面的示例中，第一次调用使用完全限定字符串。 但是，这不是必需的，因为类型提升。 第二次调用还访问模块的成员，但不将 `projModule` 包含在限定字符串中。  
  
## <a name="defeat-of-type-promotion"></a>类型提升的失效  
 如果命名空间已具有与模块成员同名的成员，则该模块成员的类型提升会失效。 下面的示例演示了枚举的主干定义和同一命名空间中的模块。  
  
 [!code-vb[VbVbalrDeclaredElements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#3)]  
  
 在前面的示例中，Visual Basic 无法将类 `abc` 提升为 `thisNameSpace`，因为在命名空间级别已存在同名的枚举。 若要访问 `abcSub`，必须使用 `thisNamespace.thisModule.abc.abcSub`的完全限定字符串。 但是，类 `xyz` 仍会升级，你可以使用较短的限定字符串 `thisNamespace.xyz.xyzSub`访问 `xyzSub`。  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a>分部类型升级类型的不足  
 如果模块内的类或结构使用[Partial](../../../../visual-basic/language-reference/modifiers/partial.md)关键字，则对于该类或结构，类型提升将自动失效，无论命名空间是否具有同名的成员。 模块中的其他元素仍适用于类型提升。  
  
 **什么.** 部分定义的类型提升的不足会导致意外的结果，甚至编译器错误。 下面的示例显示了一个类的主干分部定义，其中一个类位于模块中。  
  
 [!code-vb[VbVbalrDeclaredElements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#4)]  
  
 在前面的示例中，开发人员可能希望编译器合并 `sampleClass`的两个分部定义。 但是，编译器不会考虑 `sampleModule`中部分定义的升级。 因此，它会尝试编译两个单独的不同类，两个类都命名 `sampleClass` 但具有不同的限定路径。  
  
 仅当其完全限定的路径相同时，编译器才将合并分部定义。  
  
## <a name="recommendations"></a>建议  
 以下建议表示良好的编程做法。  
  
- **唯一名称。** 当你完全控制编程元素的命名时，在任何地方使用唯一名称始终是一个好主意。 相同的名称需要额外的限制，并且可能会使代码更难以阅读。 它们还可能导致微妙的错误和意外的结果。  
  
- **完全限定。** 使用同一个命名空间中的模块和其他元素时，最安全的方法是始终对所有编程元素使用完全限定。 如果类型提升对于某个模块成员失效，并且你未完全限定该成员，则可能会无意中访问其他编程元素。  
  
## <a name="see-also"></a>另请参阅

- [Module 语句](../../../../visual-basic/language-reference/statements/module-statement.md)
- [Namespace 语句](../../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)
- [范围 Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [如何：控制变量的范围](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [对已声明元素的引用](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
