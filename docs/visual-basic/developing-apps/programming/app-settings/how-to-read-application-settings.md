---
title: 如何：讀取應用程式設定
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: 04726381f8d285ae61045d1624b3b41b7f47e491
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329574"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a><span data-ttu-id="5855e-102">如何：在 Visual Basic 中讀取應用程式設定</span><span class="sxs-lookup"><span data-stu-id="5855e-102">How to: Read Application Settings in Visual Basic</span></span>

<span data-ttu-id="5855e-103">您可以藉由存取 `My.Settings` 物件上的設定屬性，來讀取使用者設定。</span><span class="sxs-lookup"><span data-stu-id="5855e-103">You can read a user setting by accessing the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="5855e-104">`My.Settings` 物件會將每項設定公開為屬性。</span><span class="sxs-lookup"><span data-stu-id="5855e-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="5855e-105">屬性名稱與設定名稱相同，而屬性類型與設定類型相同。</span><span class="sxs-lookup"><span data-stu-id="5855e-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="5855e-106">設定的 [範圍] 指出屬性是否為唯讀；[應用程式] 範圍設定的屬性為唯讀，而 [使用者] 範圍設定的屬性為讀寫。</span><span class="sxs-lookup"><span data-stu-id="5855e-106">The setting's **Scope** indicates if the property is read-only; the property for an **Application** scope setting is read-only, while the property for a **User** scope setting is read-write.</span></span> <span data-ttu-id="5855e-107">如需詳細資訊，請參閱 [My.Settings 物件](../../../../visual-basic/language-reference/objects/my-settings-object.md)。</span><span class="sxs-lookup"><span data-stu-id="5855e-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5855e-108">範例</span><span class="sxs-lookup"><span data-stu-id="5855e-108">Example</span></span>  

 <span data-ttu-id="5855e-109">此範例會顯示 `Nickname` 設定的值。</span><span class="sxs-lookup"><span data-stu-id="5855e-109">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="5855e-110">為了確保此範例正常運作，您的應用程式必須具有 `Nickname` 類型的 `String` 設定。</span><span class="sxs-lookup"><span data-stu-id="5855e-110">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span> <span data-ttu-id="5855e-111">如需詳細資訊，請參閱[管理應用程式設定 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="5855e-111">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5855e-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="5855e-112">See also</span></span>

- [<span data-ttu-id="5855e-113">My.Settings 物件</span><span class="sxs-lookup"><span data-stu-id="5855e-113">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="5855e-114">如何：在 Visual Basic 中變更使用者設定</span><span class="sxs-lookup"><span data-stu-id="5855e-114">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="5855e-115">如何：保存 Visual Basic 中的使用者設定</span><span class="sxs-lookup"><span data-stu-id="5855e-115">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="5855e-116">如何：在 Visual Basic 中建立使用者設定的屬性方格</span><span class="sxs-lookup"><span data-stu-id="5855e-116">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="5855e-117">管理應用程式設定 (.NET)</span><span class="sxs-lookup"><span data-stu-id="5855e-117">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
