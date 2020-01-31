---
title: 如何使用當地語系化的例外狀況訊息來建立使用者定義的例外狀況
description: 瞭解如何使用當地語系化的例外狀況訊息來建立使用者定義的例外狀況
author: Youssef1313
dev_langs:
- csharp
- vb
ms.date: 09/13/2019
ms.openlocfilehash: 48e429a6379b0a13cb81f8db6fae27aa31409840
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794617"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a><span data-ttu-id="afc26-103">如何使用當地語系化的例外狀況訊息來建立使用者定義的例外狀況</span><span class="sxs-lookup"><span data-stu-id="afc26-103">How to create user-defined exceptions with localized exception messages</span></span>

<span data-ttu-id="afc26-104">在本文中，您將瞭解如何使用附屬元件，建立繼承自基底 <xref:System.Exception> 類別的使用者定義例外狀況，以及當地語系化的例外狀況訊息。</span><span class="sxs-lookup"><span data-stu-id="afc26-104">In this article, you will learn how to create user-defined exceptions that are inherited from the base <xref:System.Exception> class with localized exception messages using satellite assemblies.</span></span>

## <a name="create-custom-exceptions"></a><span data-ttu-id="afc26-105">建立自訂例外狀況</span><span class="sxs-lookup"><span data-stu-id="afc26-105">Create custom exceptions</span></span>

<span data-ttu-id="afc26-106">.NET 包含許多您可以使用的不同例外狀況。</span><span class="sxs-lookup"><span data-stu-id="afc26-106">.NET contains many different exceptions that you can use.</span></span> <span data-ttu-id="afc26-107">不過，在某些情況下，如果它們都不符合您的需求，您可以建立自己的自訂例外狀況。</span><span class="sxs-lookup"><span data-stu-id="afc26-107">However, in some cases when none of them meets your needs, you can create your own custom exceptions.</span></span>

<span data-ttu-id="afc26-108">假設您想要建立包含 `StudentName` 屬性的 `StudentNotFoundException`。</span><span class="sxs-lookup"><span data-stu-id="afc26-108">Let's assume you want to create a `StudentNotFoundException` that contains a `StudentName` property.</span></span>
<span data-ttu-id="afc26-109">若要建立自訂例外狀況，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="afc26-109">To create a custom exception, follow these steps:</span></span>

1. <span data-ttu-id="afc26-110">建立繼承自 <xref:System.Exception>的可序列化類別。</span><span class="sxs-lookup"><span data-stu-id="afc26-110">Create a serializable class that inherits from <xref:System.Exception>.</span></span> <span data-ttu-id="afc26-111">類別名稱的結尾應該是 "Exception"：</span><span class="sxs-lookup"><span data-stu-id="afc26-111">The class name should end in "Exception":</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception { }
    ```
    
    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception
    End Class
    ```

1. <span data-ttu-id="afc26-112">新增預設的構造函式：</span><span class="sxs-lookup"><span data-stu-id="afc26-112">Add the default constructors:</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception
    {
        public StudentNotFoundException() { }

        public StudentNotFoundException(string message)
            : base(message) { }

        public StudentNotFoundException(string message, Exception inner)
            : base(message, inner) { }
    }
    ```
    
    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception

        Public Sub New()
        End Sub

        Public Sub New(message As String)
            MyBase.New(message)
        End Sub

        Public Sub New(message As String, inner As Exception)
            MyBase.New(message, inner)
        End Sub
    End Class
    ```

1. <span data-ttu-id="afc26-113">定義任何其他屬性和構造函式：</span><span class="sxs-lookup"><span data-stu-id="afc26-113">Define any additional properties and constructors:</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception
    {
        public string StudentName { get; }

        public StudentNotFoundException() { }

        public StudentNotFoundException(string message)
            : base(message) { }

        public StudentNotFoundException(string message, Exception inner)
            : base(message, inner) { }

        public StudentNotFoundException(string message, string studentName)
            : this(message)
        {
            StudentName = studentName;
        }
    }
    ```

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception

        Public ReadOnly Property StudentName As String

        Public Sub New()
        End Sub

        Public Sub New(message As String)
            MyBase.New(message)
        End Sub

        Public Sub New(message As String, inner As Exception)
            MyBase.New(message, inner)
        End Sub

        Public Sub New(message As String, studentName As String)
            Me.New(message)
            StudentName = studentName
        End Sub
    End Class
    ```

## <a name="create-localized-exception-messages"></a><span data-ttu-id="afc26-114">建立當地語系化的例外狀況訊息</span><span class="sxs-lookup"><span data-stu-id="afc26-114">Create localized exception messages</span></span>

<span data-ttu-id="afc26-115">您已建立自訂例外狀況，您可以使用類似下列的程式碼在任何地方擲回它：</span><span class="sxs-lookup"><span data-stu-id="afc26-115">You have created a custom exception, and you can throw it anywhere with code like the following:</span></span>

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

```vb
Throw New StudentNotFoundException("The student cannot be found.", "John")
```

<span data-ttu-id="afc26-116">前一行的問題在於，`"The student cannot be found."` 只是一個常數位串。</span><span class="sxs-lookup"><span data-stu-id="afc26-116">The problem with the previous line is that `"The student cannot be found."` is just a constant string.</span></span> <span data-ttu-id="afc26-117">在當地語系化的應用程式中，您想要根據使用者文化特性來擁有不同的訊息。</span><span class="sxs-lookup"><span data-stu-id="afc26-117">In a localized application, you want to have different messages depending on user culture.</span></span>
<span data-ttu-id="afc26-118">[附屬元件](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)是執行這項操作的好方法。</span><span class="sxs-lookup"><span data-stu-id="afc26-118">[Satellite Assemblies](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) are a good way to do that.</span></span> <span data-ttu-id="afc26-119">附屬元件是包含特定語言之資源的 .dll。</span><span class="sxs-lookup"><span data-stu-id="afc26-119">A satellite assembly is a .dll that contains resources for a specific language.</span></span> <span data-ttu-id="afc26-120">當您在執行時間要求特定資源時，CLR 會根據使用者文化特性來尋找該資源。</span><span class="sxs-lookup"><span data-stu-id="afc26-120">When you ask for a specific resources at run time, the CLR finds that resource depending on user culture.</span></span> <span data-ttu-id="afc26-121">如果找不到該文化特性的附屬元件，則會使用預設文化特性的資源。</span><span class="sxs-lookup"><span data-stu-id="afc26-121">If no satellite assembly is found for that culture, the resources of the default culture are used.</span></span>

<span data-ttu-id="afc26-122">若要建立當地語系化的例外狀況訊息：</span><span class="sxs-lookup"><span data-stu-id="afc26-122">To create the localized exception messages:</span></span>

1. <span data-ttu-id="afc26-123">建立名為*Resources*的新資料夾來存放資源檔。</span><span class="sxs-lookup"><span data-stu-id="afc26-123">Create a new folder named *Resources* to hold the resource files.</span></span>
1. <span data-ttu-id="afc26-124">在其中加入新的資源檔。</span><span class="sxs-lookup"><span data-stu-id="afc26-124">Add a new resource file to it.</span></span> <span data-ttu-id="afc26-125">若要在 Visual Studio 中執行此動作，請以滑鼠右鍵按一下**方案總管**中的資料夾，**然後選取 [** 新增 > **新專案** > **資源檔**]。</span><span class="sxs-lookup"><span data-stu-id="afc26-125">To do that in Visual Studio, right-click the folder in **Solution Explorer**, and select **Add** > **New Item** > **Resources File**.</span></span> <span data-ttu-id="afc26-126">將檔案命名為*ExceptionMessages .resx*。</span><span class="sxs-lookup"><span data-stu-id="afc26-126">Name the file *ExceptionMessages.resx*.</span></span> <span data-ttu-id="afc26-127">這是預設的資源檔。</span><span class="sxs-lookup"><span data-stu-id="afc26-127">This is the default resources file.</span></span>
1. <span data-ttu-id="afc26-128">新增例外狀況訊息的名稱/值組，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="afc26-128">Add a name/value pair for your exception message, like the following image shows:</span></span>

   ![將資源新增至預設文化特性](media/add-resources-to-default-culture.jpg)

1. <span data-ttu-id="afc26-130">新增法文的新資源檔。</span><span class="sxs-lookup"><span data-stu-id="afc26-130">Add a new resource file for French.</span></span> <span data-ttu-id="afc26-131">將它命名*為 ExceptionMessages.fr-fr .resx*。</span><span class="sxs-lookup"><span data-stu-id="afc26-131">Name it *ExceptionMessages.fr-FR.resx*.</span></span>
1. <span data-ttu-id="afc26-132">再次新增例外狀況訊息的名稱/值組，但使用法文值：</span><span class="sxs-lookup"><span data-stu-id="afc26-132">Add a name/value pair for the exception message again, but with a French value:</span></span>

   ![將資源新增至 fr-fr 文化特性](media/add-resources-to-fr-culture.jpg)

1. <span data-ttu-id="afc26-134">在您建立專案之後，組建輸出檔案夾應該包含*fr-fr*資料夾，其為 *.dll*檔案，也就是附屬元件。</span><span class="sxs-lookup"><span data-stu-id="afc26-134">After you build the project, the build output folder should contain the *fr-FR* folder with a *.dll* file, which is the satellite assembly.</span></span>
1. <span data-ttu-id="afc26-135">您會擲回例外狀況，其程式碼如下所示：</span><span class="sxs-lookup"><span data-stu-id="afc26-135">You throw the exception with code like the following:</span></span>

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

    ```vb
    Dim resourceManager As New ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly())
    Throw New StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John")
    ```

    > [!NOTE]
    > <span data-ttu-id="afc26-136">如果專案名稱是 `TestProject`，而資源檔*ExceptionMessages*位於專案的*Resources*資料夾中，則資源檔的完整名稱會是 `TestProject.Resources.ExceptionMessages`。</span><span class="sxs-lookup"><span data-stu-id="afc26-136">If the project name is `TestProject` and the resource file *ExceptionMessages.resx* resides in the *Resources* folder of the project, the fully qualified name of the resource file is `TestProject.Resources.ExceptionMessages`.</span></span>

## <a name="see-also"></a><span data-ttu-id="afc26-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="afc26-137">See also</span></span>

- [<span data-ttu-id="afc26-138">如何建立使用者定義的例外狀況</span><span class="sxs-lookup"><span data-stu-id="afc26-138">How to create user-defined exceptions</span></span>](how-to-create-user-defined-exceptions.md)
- [<span data-ttu-id="afc26-139">建立桌面應用程式的附屬元件</span><span class="sxs-lookup"><span data-stu-id="afc26-139">Creating Satellite Assemblies for Desktop Apps</span></span>](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [<span data-ttu-id="afc26-140">基底C# （參考）</span><span class="sxs-lookup"><span data-stu-id="afc26-140">base (C# Reference)</span></span>](../../csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="afc26-141">this （C#參考）</span><span class="sxs-lookup"><span data-stu-id="afc26-141">this (C# Reference)</span></span>](../../csharp/language-reference/keywords/this.md)
