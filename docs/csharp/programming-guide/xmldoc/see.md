---
title: <see> - C# 程式設計指南
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: 995b67362bccbc3527f44e5a1d6b659f330e3afd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711710"
---
# <a name="see-c-programming-guide"></a>\<see> (C# 程式設計指南)
## <a name="syntax"></a>語法  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a>參數  
 cref = " `member`"  
 可從目前編譯環境呼叫的成員或欄位參考。 編譯器會檢查指定的程式碼項目是否存在，並將 `member` 傳遞給輸出 XML 中的項目名稱。 將 *member* 置於雙引號 (" ") 內。  
  
## <a name="remarks"></a>備註  
 \<see> 標記可讓您在文字內指定連結。 使用 [\<seealso>](./seealso.md) 指出文字應該放置於＜請參閱＞一節中。 使用 [cref 屬性](./cref-attribute.md)，建立程式碼項目之文件頁面的內部超連結。  
  
 使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 編譯可處理檔案的文件註解。  
  
 下列範例示範摘要區段內的 \<see> 標記。  
  
 [!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]  
  
## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../index.md)
- [建議使用的文件註解標籤](./recommended-tags-for-documentation-comments.md)
