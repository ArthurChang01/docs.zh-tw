---
title: 字串插值
ms.date: 10/31/2017
ms.openlocfilehash: d1220f3804d571f6da229dc5dfa099a22ab1478d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344318"
---
# <a name="interpolated-strings-visual-basic-reference"></a><span data-ttu-id="a6bf2-102">Interpolated Strings (Visual Basic Reference)</span><span class="sxs-lookup"><span data-stu-id="a6bf2-102">Interpolated Strings (Visual Basic Reference)</span></span>

<span data-ttu-id="a6bf2-103">可用來建構字串。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-103">Used to construct strings.</span></span>  <span data-ttu-id="a6bf2-104">字串插值類似包含「插入運算式」的範本字串。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-104">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span>  <span data-ttu-id="a6bf2-105">字串插值會傳回一個字串，以將內含的插入運算式取代為運算式的字串表示。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-105">An interpolated string returns a string that replaces the interpolated expressions that it contains with their string representations.</span></span> <span data-ttu-id="a6bf2-106">This feature is available in Visual Basic 14 and later versions.</span><span class="sxs-lookup"><span data-stu-id="a6bf2-106">This feature is available in Visual Basic 14 and later versions.</span></span>

<span data-ttu-id="a6bf2-107">字串插值的引數比[複合格式字串](../../../../standard/base-types/composite-formatting.md#composite-format-string)更容易了解。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-107">The arguments of an interpolated string are easier to understand than a [composite format string](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span></span>  <span data-ttu-id="a6bf2-108">例如，字串插值</span><span class="sxs-lookup"><span data-stu-id="a6bf2-108">For example, the interpolated string</span></span>

```vb
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```

<span data-ttu-id="a6bf2-109">包含兩個插入運算式 '{name}' 和 '{hours:hh}'。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-109">contains two interpolated expressions, '{name}' and '{hours:hh}'.</span></span> <span data-ttu-id="a6bf2-110">對等的複合格式字串為：</span><span class="sxs-lookup"><span data-stu-id="a6bf2-110">The equivalent composite format string is:</span></span>

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours)
```

<span data-ttu-id="a6bf2-111">字串插值的結構為：</span><span class="sxs-lookup"><span data-stu-id="a6bf2-111">The structure of an interpolated string is:</span></span>

```vb
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."
```

<span data-ttu-id="a6bf2-112">其中：</span><span class="sxs-lookup"><span data-stu-id="a6bf2-112">where:</span></span>

- <span data-ttu-id="a6bf2-113">*field-width* 是帶正負號的整數，表示欄位中的字元數。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-113">*field-width* is a signed integer that indicates the number of characters in the field.</span></span> <span data-ttu-id="a6bf2-114">如果是正數，則欄位會靠右對齊；如果是負數，則會靠左對齊。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-114">If it is positive, the field is right-aligned; if negative, left-aligned.</span></span>

- <span data-ttu-id="a6bf2-115">*format-string* 是一個格式字串，適用於將格式化的物件類型。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-115">*format-string* is a format string appropriate for the type of object being formatted.</span></span> <span data-ttu-id="a6bf2-116">For example, for a <xref:System.DateTime> value, it could be a [standard date and time format string](../../../../standard/base-types/standard-date-and-time-format-strings.md) such as "D" or "d".</span><span class="sxs-lookup"><span data-stu-id="a6bf2-116">For example, for a <xref:System.DateTime> value, it could be a [standard date and time format string](../../../../standard/base-types/standard-date-and-time-format-strings.md) such as "D" or "d".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a6bf2-117">字串開頭的 `$` 與 `"` 之間不能有空白字元。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-117">You cannot have any white space between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="a6bf2-118">Doing so causes a compiler error.</span><span class="sxs-lookup"><span data-stu-id="a6bf2-118">Doing so causes a compiler error.</span></span>

<span data-ttu-id="a6bf2-119">您可以在使用字串常值的任何位置使用字串插值。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-119">You can use an interpolated string anywhere you can use a string literal.</span></span>  <span data-ttu-id="a6bf2-120">每次執行含有字串插值的程式碼時，都會評估字串插值。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-120">The interpolated string is evaluated each time the code with the interpolated string executes.</span></span> <span data-ttu-id="a6bf2-121">這可讓您分開定義和評估字串插值。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-121">This allows you to separate the definition and evaluation of an interpolated string.</span></span>

<span data-ttu-id="a6bf2-122">若要在字串插值中包含大括弧 ("{" 或 "}")，請使用雙大括弧 "{{" 或 "}}"。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-122">To include a curly brace ("{" or "}") in an interpolated string, use two curly braces, "{{" or "}}".</span></span>  <span data-ttu-id="a6bf2-123">如需詳細資訊，請參閱＜隱含轉換＞一節。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-123">See the Implicit Conversions section for more details.</span></span>

<span data-ttu-id="a6bf2-124">當字串插值包含在字串插值中具有特殊意義的其他字元時 (例如引號 (")、冒號 (:) 或逗號 (,))，如果這些字元出現在常值文字中，則必須將它逸出；如果這些字元是包含在插入運算式中的語言項目，則必須加入以括號分隔的運算式。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-124">If the interpolated string contains other characters with special meaning in an interpolated string, such as the quotation mark ("), colon (:), or comma (,), they should be escaped if they occur in literal text, or they should be included in an expression delimited by parentheses if they are language elements included in an interpolated expression.</span></span> <span data-ttu-id="a6bf2-125">下列範例會將引號逸出，以在結果字串中包含這些引號，而且會使用括號來分隔運算式 `(age == 1 ? "" : "s")`，以防止將冒號解譯為格式字串的開頭。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-125">The following example escapes quotation marks to include them in the result string, and it uses parentheses to delimit the expression `(age == 1 ? "" : "s")` so that the colon is not interpreted as beginning a format string.</span></span>

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]

## <a name="implicit-conversions"></a><span data-ttu-id="a6bf2-126">隱含轉換</span><span class="sxs-lookup"><span data-stu-id="a6bf2-126">Implicit Conversions</span></span>

<span data-ttu-id="a6bf2-127">有三個來自字串插值的隱含型別轉換：</span><span class="sxs-lookup"><span data-stu-id="a6bf2-127">There are three implicit type conversions from an interpolated string:</span></span>

1. <span data-ttu-id="a6bf2-128">將字串插值轉換成 <xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-128">Conversion of an interpolated string to a <xref:System.String>.</span></span> <span data-ttu-id="a6bf2-129">下列範例會傳回一個字串，其字串插值運算式已取代為運算式的字串表示。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-129">The following example returns a string whose interpolated string expressions have been replaced with their string representations.</span></span> <span data-ttu-id="a6bf2-130">例如:</span><span class="sxs-lookup"><span data-stu-id="a6bf2-130">For example:</span></span>

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]

   <span data-ttu-id="a6bf2-131">這是字串解譯的最終結果。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-131">This is the final result of a string interpretation.</span></span> <span data-ttu-id="a6bf2-132">所有出現的雙大括弧 ("{{" 和 "}}") 都會轉換成單一大括弧。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-132">All occurrences of double curly braces ("{{" and "}}") are converted to a single curly brace.</span></span>

2. <span data-ttu-id="a6bf2-133">將字串插值轉換成 <xref:System.IFormattable> 變數，可讓您從單一 <xref:System.IFormattable> 執行個體建立多個具有特定文化特性內容的結果字串。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-133">Conversion of an interpolated string to an <xref:System.IFormattable> variable that allows you create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span> <span data-ttu-id="a6bf2-134">若要加入個別文化特性的正確數值和日期格式等項目時，這樣做會很有用。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-134">This is useful for including such things as the correct numeric and date formats for individual cultures.</span></span>  <span data-ttu-id="a6bf2-135">在您明確或隱含呼叫 <xref:System.Object.ToString> 方法以格式化字串之前，所有出現的雙大括弧 ("{{" 和 "}}") 會保持為雙大括弧。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-135">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format the string by explicitly or implicitly calling the <xref:System.Object.ToString> method.</span></span>  <span data-ttu-id="a6bf2-136">All contained interpolation expressions are converted to {0}, {1}, and so on.</span><span class="sxs-lookup"><span data-stu-id="a6bf2-136">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>

   <span data-ttu-id="a6bf2-137">下列範例使用反映來顯示成員，以及從字串插值建立之 <xref:System.IFormattable> 變數的欄位和屬性值。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-137">The following example uses reflection to display the members as well as the field and property values of an <xref:System.IFormattable> variable that is created from an interpolated string.</span></span> <span data-ttu-id="a6bf2-138">它也會將 <xref:System.IFormattable> 變數傳遞給 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-138">It also passes the <xref:System.IFormattable> variable to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method.</span></span>

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]

   <span data-ttu-id="a6bf2-139">請注意，只能使用反映來檢查字串插值。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-139">Note that the interpolated string can be inspected only by using reflection.</span></span> <span data-ttu-id="a6bf2-140">如果將它傳遞至字串格式化方法 (例如 <xref:System.Console.WriteLine(System.String)>)，則會解析其格式項目並傳回結果字串。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-140">If it is passed to a string formatting method, such as <xref:System.Console.WriteLine(System.String)>, its format items are resolved and the result string returned.</span></span>

3. <span data-ttu-id="a6bf2-141">Conversion of an interpolated string to a <xref:System.FormattableString> variable that represents a composite format string.</span><span class="sxs-lookup"><span data-stu-id="a6bf2-141">Conversion of an interpolated string to a <xref:System.FormattableString> variable that represents a composite format string.</span></span> <span data-ttu-id="a6bf2-142">檢查複合格式字串及其如何轉譯為結果字串有助於在建立查詢時，防止插入式攻擊。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-142">Inspecting the composite format string and how it renders as a result string might, for example, help you protect against an injection attack if you were building a query.</span></span> <span data-ttu-id="a6bf2-143">A <xref:System.FormattableString> also includes:</span><span class="sxs-lookup"><span data-stu-id="a6bf2-143">A <xref:System.FormattableString> also includes:</span></span>

      - <span data-ttu-id="a6bf2-144">產生 <xref:System.Globalization.CultureInfo.CurrentCulture> 的結果字串的 <xref:System.FormattableString.ToString> 多載。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-144">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>

      - <span data-ttu-id="a6bf2-145">A <xref:System.FormattableString.Invariant%2A> method that produces a string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="a6bf2-145">A <xref:System.FormattableString.Invariant%2A> method that produces a string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>

      - <span data-ttu-id="a6bf2-146">產生指定文化特性的結果字串的 <xref:System.FormattableString.ToString(System.IFormatProvider)> 方法。</span><span class="sxs-lookup"><span data-stu-id="a6bf2-146">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

    <span data-ttu-id="a6bf2-147">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format.</span><span class="sxs-lookup"><span data-stu-id="a6bf2-147">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format.</span></span>  <span data-ttu-id="a6bf2-148">All contained interpolation expressions are converted to {0}, {1}, and so on.</span><span class="sxs-lookup"><span data-stu-id="a6bf2-148">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]

## <a name="see-also"></a><span data-ttu-id="a6bf2-149">請參閱</span><span class="sxs-lookup"><span data-stu-id="a6bf2-149">See also</span></span>

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- [<span data-ttu-id="a6bf2-150">Visual Basic 語言參考</span><span class="sxs-lookup"><span data-stu-id="a6bf2-150">Visual Basic Language Reference</span></span>](index.md)
