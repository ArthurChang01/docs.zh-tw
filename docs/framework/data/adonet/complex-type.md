---
title: 複雜類型
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: e21ca90a7be8f2bd9be9483c66a1e95e6ba1bee2
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738544"
---
# <a name="complex-type"></a><span data-ttu-id="bbc90-102">複雜類型</span><span class="sxs-lookup"><span data-stu-id="bbc90-102">complex type</span></span>
<span data-ttu-id="bbc90-103">「*複雜類型」（complex type* ）是在[實體類型](entity-type.md)或其他複雜類型上定義豐富結構化屬性的範本。</span><span class="sxs-lookup"><span data-stu-id="bbc90-103">A *complex type* is a template for defining rich, structured properties on [entity types](entity-type.md) or on other complex types.</span></span> <span data-ttu-id="bbc90-104">每個範本包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="bbc90-104">Each template contains the following:</span></span>  
  
- <span data-ttu-id="bbc90-105">唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="bbc90-105">A unique name.</span></span> <span data-ttu-id="bbc90-106">(必要項)</span><span class="sxs-lookup"><span data-stu-id="bbc90-106">(Required)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="bbc90-107">複雜類型的名稱不可以與同一個命名空間中的實體類型名稱相同。</span><span class="sxs-lookup"><span data-stu-id="bbc90-107">The name of a complex type cannot be the same as an entity type name within the same namespace.</span></span>  
  
- <span data-ttu-id="bbc90-108">一或多個[屬性](property.md)形式的資料。</span><span class="sxs-lookup"><span data-stu-id="bbc90-108">Data in the form of one or more [properties](property.md).</span></span> <span data-ttu-id="bbc90-109">(選擇性。)</span><span class="sxs-lookup"><span data-stu-id="bbc90-109">(Optional.)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="bbc90-110">複雜類型的屬性可以是另一個複雜類型。</span><span class="sxs-lookup"><span data-stu-id="bbc90-110">A property of a complex type can be another complex type.</span></span>  
  
 <span data-ttu-id="bbc90-111">複雜類型與實體類型相似之處在於，複雜類型可以包含基本型別屬性或其他複雜類型形式的資料承載。</span><span class="sxs-lookup"><span data-stu-id="bbc90-111">A complex type is similar to an entity type in that a complex type can carry a data payload in the form of primitive type properties or other complex types.</span></span> <span data-ttu-id="bbc90-112">不過，複雜型別和實體類型之間還是有些重大的差異：</span><span class="sxs-lookup"><span data-stu-id="bbc90-112">However, there are some key differences between complex types and entity types:</span></span>  
  
- <span data-ttu-id="bbc90-113">複雜類型不具有識別，因此無法獨立存在。</span><span class="sxs-lookup"><span data-stu-id="bbc90-113">Complex types do not have identities and therefore cannot exist independently.</span></span> <span data-ttu-id="bbc90-114">複雜類型只能以實體類型或其他複雜類型的屬性形式存在。</span><span class="sxs-lookup"><span data-stu-id="bbc90-114">Complex types can only exist as properties on entity types or other complex types.</span></span>  
  
- <span data-ttu-id="bbc90-115">複雜類型不能參與[關聯](association-type.md)。</span><span class="sxs-lookup"><span data-stu-id="bbc90-115">Complex types cannot participate in [associations](association-type.md).</span></span> <span data-ttu-id="bbc90-116">關聯的兩端都不可以是複雜類型，因此無法在複雜類型上定義[導覽屬性](navigation-property.md)。</span><span class="sxs-lookup"><span data-stu-id="bbc90-116">Neither end of an association can be a complex type, and therefore [navigation properties](navigation-property.md) cannot be defined on complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbc90-117">範例</span><span class="sxs-lookup"><span data-stu-id="bbc90-117">Example</span></span>  
 <span data-ttu-id="bbc90-118">[ADO.NET Entity Framework](./ef/index.md)會使用稱為概念結構定義語言（[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)）的特定領域語言（DSL）來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="bbc90-118">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="bbc90-119">下列 CSDL 以基底類型屬性 `StreetAddress`、`City`、`StateOrProvince`、`Country` 和 `PostalCode` 定義複雜類型 Address。</span><span class="sxs-lookup"><span data-stu-id="bbc90-119">The following CSDL defines a complex type, Address, with the primitive type properties `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 <span data-ttu-id="bbc90-120">若要將上方的複雜類型 `Address` 定義為實體類型上的屬性，您必須在實體類型定義中宣告屬性型別。</span><span class="sxs-lookup"><span data-stu-id="bbc90-120">To define the complex type `Address` (above) as a property on an entity type, you must declare the property type in the entity type definition.</span></span> <span data-ttu-id="bbc90-121">下列 CSDL 會在實體類型 (Publisher) 上將 `Address` 屬性宣告為複雜類型：</span><span class="sxs-lookup"><span data-stu-id="bbc90-121">The following CSDL declares the `Address` property as a complex type on an entity type (Publisher):</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a><span data-ttu-id="bbc90-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="bbc90-122">See also</span></span>

- [<span data-ttu-id="bbc90-123">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="bbc90-123">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="bbc90-124">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="bbc90-124">Entity Data Model</span></span>](entity-data-model.md)
