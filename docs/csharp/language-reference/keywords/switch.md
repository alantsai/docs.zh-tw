---
title: "switch 關鍵字 (C# 參考)"
ms.date: 2017-03-07
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- switch_CSharpKeyword
- switch
- case
- case_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- switch statement [C#]
- switch keyword [C#]
- case statement [C#]
- default keyword [C#]
ms.assetid: 44bae8b8-8841-4d85-826b-8a94277daecb
caps.latest.revision: 47
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 387c8c7e44ab818ca97e686330746f50df091bb9
ms.openlocfilehash: 5c151e3bbd46212f1234d46ff05d389f2384ca0e
ms.contentlocale: zh-tw
ms.lasthandoff: 08/01/2017

---
# <a name="switch-c-reference"></a>switch (C# 參考)
`switch` 是一個選取範圍陳述式，可根據使用「比對運算式」**的模式比對，從候選項清單中選擇要執行的單一「參數區段」**。 
  
 [!code-cs[switch#1](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]  

如果針對三個或多個條件測試單一運算式，則通常會使用 `switch` 陳述式來替代 [if-else](if-else.md) 建構。 例如，下列 `switch` 陳述式判斷 `Color` 類型的變數是否有三個值之一︰ 

[!code-cs[switch#3](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)] 

它等同於下列使用 `if`-`else` 建構的範例。 

[!code-cs[switch#3a](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)] 

## <a name="the-match-expression"></a>比對運算式

比對運算式提供要與 `case` 標籤中的模式進行比對的值。 它的語法為：

```csharp
   switch (expr)
```

在 C# 6 中，比對運算式必須是傳回下列類型之值的運算式︰

- [char](char.md)。
- [string](string.md)。
- [bool](bool.md)。 
- 整數值，例如 [int](int.md) 或 [long](long.md)。
- [enum](enum.md) 值。

從 C# 7 開始，比對運算式可以是任何非 Null 運算式。
 
## <a name="the-switch-section"></a>參數區段
 
 `switch` 陳述式包含一個或多個參數區段。 每個參數區段都包含一或多個*「case 標籤」*，後面接著一或多個陳述式。 下列範例將示範擁有三個參數區段的簡單 `switch` 陳述式。 每個參數區段擁有一個 case 標籤，例如 `case 1:`，以及兩個陳述式。
 
  `switch` 陳述式可包含任意數目的參數區段，而每個區段都可以擁有一或多個 case 標籤，如下列範例所示。 不過，不可以有兩個 case 標籤包含相同的運算式。  

 [!code-cs[switch#2](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]  

 switch 陳述式中只會執行一個參數區段。 C# 不允許從某個參數區段繼續執行至另一個參數區段。 因此，下列程式碼會產生編譯器錯誤 CS0163：「程式控制權無法從一個 case 標籤 (<case label>) 繼續到另一個」。   

```csharp  
switch (caseSwitch)  
{  
    // The following switch section causes an error.  
    case 1:  
        Console.WriteLine("Case 1...");  
        // Add a break or other jump statement here.  
    case 2:  
        Console.WriteLine("... and/or Case 2");  
        break;  
}  
```  
使用 [break](break.md)、[goto](goto.md) 或 [return](return.md) 陳述式明確地結束參數區段，通常會符合這項需求。 不過，下列程式碼也是有效，因為它可確保程式控制權無法切換到 `default` 參數區段。
  
 [!code-cs[switch#4](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]    
  
 在 case 標籤符合比對運算式的參數區段中，陳述式清單是從第一個陳述式開始執行，然後繼續進行整份陳述式清單，通常會進行直到跳躍陳述式為止，例如到達 `break`、`goto case`、`goto label`、`return` 或 `throw`。 到達該點時，控制項會在 `switch` 陳述式之外傳輸，或傳輸至另一個 case 標籤。 如果使用 `goto` 陳述式，就必須將控制權轉移到常數標籤。 這項限制是必要的，因為嘗試將控制項傳送至非常數標籤，會將控制項傳送至程式碼中非預期的位置或建立無止盡的迴圈，出現非預期的副作用。

## <a name="case-labels"></a>case 標籤

 每個 case 標籤都會指定要與比對運算式比較的模式 (先前範例中的 `caseSwitch` 變數)。 如果相符，控制權會轉移至**「第一個」**相符 case 標籤的參數區段。 如果沒有任何 case 標籤模式符合比對運算式，則控制權會轉移到具有 `default` case 標籤 (如果有的話) 的區段。 如果沒有 `default` case，則不會執行任何參數區段中的陳述式，而且控制權會轉移到 `switch` 陳述式外部。

 如需 `switch` 陳述式和模式比對的資訊，請參閱[模式比對與 `switch` 陳述式](#pattern)一節。

 因為 C# 6 只支援常數模式，且不允許重複常數值，所以 case 標籤定義互斥值，而且只有一個模式可以符合比對運算式。 因此，`case` 陳述式的出現順序並不重要。

 不過，在 C# 7 中，因為支援其他模式，所以 case 標籤不需要定義互斥值，而且可以有多個模式符合比對運算式。 因為只會執行包含第一個相符模式的參數區段中的陳述式，所以 `case` 陳述式的出現順序現在十分重要。 如果 C# 偵測到一或多個 case 陳述式等於或為先前陳述式子集的參數區段，則會產生編譯器錯誤 CS8120：「先前的案例已處理切換案例。」 

 下列範例說明使用各種非互斥模式的 `switch` 陳述式。 如果您移動 `case 0:` 參數區段，讓它不再是 `switch` 陳述式中的第一個區段，則 C# 會產生編譯器錯誤，因為值為零的整數是所有整數的子集，而這是 `case int val` 陳述式所定義的模式。

 [!code-cs[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]    

您可以更正此問題，並使用兩種方式之一來排除編譯器警告︰

- 變更參數區段的順序。 
 
- 在 `case` 標籤中使用 </a name="when">when 子句</a>。
 
## <a name="the-default-case"></a>`default` case

如果比對運算式不符合任何其他 `case` 標籤，則 `default` case 指定要執行的參數區段。 如果 `default` case 不存在，而且比對運算式不符合任何其他 `case` 標籤，則程式流程會落到 `switch` 陳述式。

`default` case 可以依任何順序出現在 `switch` 陳述式中。 不論它在原始程式碼中的順序為何，一律都會在評估過所有 `case` 標籤之後最後才進行評估。

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a>使用 `switch` 陳述式進行的 <a name="pattern" /> 模式比對
  
每個 `case` 陳述式都會定義一個模式，並在模式符合比對運算式時，執行其包含參數區段。 所有版本的 C# 都支援常數模式。 從 C# 7 開始，支援其餘的模式。 
  
### <a name="constant-pattern"></a>常數模式 

常數模式會測試比對運算式是否等於指定的常數。 它的語法為：

```csharp
   case constant:
```

其中，*constant* 是用來測試的值。 *constant* 可以是下列任何常數運算式： 

- [bool](bool.md) 常值：`true` 或 `false`。
- 任何整數常數，例如 [int](int.md)、[long](long.md) 或 [byte](byte.md)。 
- 所宣告之 `const` 變數的名稱。
- 列舉常數。
- [char](char.md) 常值。
- [string](string.md) 常值。

常數運算式評估如下：

- 如果 *expr* 和 *constant* 是整數型別，則 C# 等號比較運算子會判斷運算式是否傳回 `true` (亦即是否 `expr == constant`)。

- 否則，會呼叫靜態 [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) 方法來判斷運算式的值。  

下列範例使用常數模式，來判斷特定日期是週末、工作週的第一天、工作週的最後一天，還是工作週的中間一天。 它會針對 @System.DayOfWeek 列舉的成員來評估目前這天的 [DateTime.DayOfWeek](xref:System.DateTime.DayOfWeek) 屬性。 

[!code-cs[switch#7](../../../../samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

下列範例使用常數模式，來處理模擬自動咖啡機之主控台應用程式中的使用者輸入。
  
 [!code-cs[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]  

### <a name="type-pattern"></a>類型模式

類型模式會啟用精簡類型評估和轉換。 與 `switch` 陳述式搭配使用來執行模式比對時，會測試運算式是否可轉換成指定的類型；如果可以的話，則會將它轉換成該類型的變數。 它的語法為：

```csharp
   case type varname 
```
其中，如果比對成功，則 *type* 是 *expr* 的結果要轉換的目標類型名稱，而 *varname* 是 *expr* 的結果所轉換的目標物件。 

如果符合下列任一項，則 `case` 運算式為`true`：

- *expr* 是其類型與 *type* 相同的執行個體。

- *expr* 是衍生自 *type* 的類型執行個體。 換句話說，*expr* 的結果可向上轉型成 *type* 的執行個體。

- *expr* 的編譯時期類型為 *type* 的基底類別，而 *expr* 的執行階段類型為 *type* 或衍生自 *type*。 變數的「編譯時期類型」**是定義於其型別宣告的變數類型。 變數的「執行階段類型」**是指派給該變數的執行個體類型。

- *expr* 是實作 *type* 介面的類型執行個體。

如果 case 運算式為 true，則 *varname* 會明確地進行指派，並且只具有參數區段內的區域範圍。

請注意，`null` 不符合類型。 若要比對 `null`，請使用下列 `case` 標籤︰

```csharp
case null:
```
 
下列範例使用類型模式提供各種集合類型的資訊。

[!code-cs[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

如果沒有模式比對，此程式碼可能會撰寫如下。 使用類型模式比對時，不需要測試轉換的結果是否為 `null` 或執行重複轉換，因此會產生更精簡且容易閱讀的程式碼。  

[!code-cs[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="the-case-statement-and-the-when-clause"></a>`case` 陳述式和 `when` 子句

從 C# 7 開始，因為 case 陳述式不需要互斥，所以您可以新增 `when` 子句來指定其他條件，您必須滿足這些條件，case 陳述式才會評估為 true。 `when` 子句可以是任何傳回布林值的運算式。 其中一個更常用的 `when` 子句是用來防止在比對運算式的值為 `null` 時執行參數區段。 

 下面範例定義基底 `Shape` 類別、衍生自 `Shape` 的 `Rectangle` 類別，以及衍生自 `Rectangle` 的 `Square` 類別。 它會使用 `when` 子句，確保 `ShowShapeInfo` 將已指派相等長度和寬度的 `Rectangle` 物件識別為 `Square`，即使尚未具現化為 `Square` 物件也是一樣。 此方法不會嘗試顯示為 `null` 的物件或區域為零之組織結構的相關資訊。 

[!code-cs[switch#8](../../../../samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]
  
請注意，不會執行範例中嘗試測試 `Shape` 物件是否為 `null` 的 `when` 子句。 要測試是否為 `null` 的正確類型模式是 `case null:`。

## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>另請參閱  

 [C# 參考](../index.md)   
 [C# 程式設計手冊](../../programming-guide/index.md)   
 [C# 關鍵字](index.md)   
 [if-else](if-else.md)   
 [模式比對](../../pattern-matching.md)   
 

 

