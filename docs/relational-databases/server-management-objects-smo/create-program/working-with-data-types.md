---
title: "データ型の使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- DataType object
- SQL Server Management Objects, data types
- data types [SMO]
- SMO [SQL Server], data types
ms.assetid: 1e0e736a-c709-4d89-aeb2-b32dcfd641fa
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 575e2b0553bd37ca095c1864cc775547ace36a76
ms.sourcegitcommit: cb2f9d4db45bef37c04064a9493ac2c1d60f2c22
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/12/2018
---
# <a name="working-with-data-types"></a>データ型の処理
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  データは、定義済みの長さを持つ文字列、特定の精度を持つ数値、または独自のルール セットを持つ別のオブジェクトであるユーザー定義データ型など、さまざまな型およびサイズで表現されます。 <xref:Microsoft.SqlServer.Management.Smo.DataType>をによって適切に処理できるように、オブジェクトがデータの種類を分類[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。 <xref:Microsoft.SqlServer.Management.Smo.DataType> オブジェクトは、データを受け入れるオブジェクトに関連付けられています。 次[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]管理オブジェクト (SMO) オブジェクトに渡すデータによって定義する必要があります、<xref:Microsoft.SqlServer.Management.Smo.DataType>オブジェクトのプロパティ。  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Column>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunctionParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunctionParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedAggregateParameter>  
  
 データを受け入れるオブジェクトの **DataType** プロパティは、次のいくつかの方法で設定することができます。  
  
-   既定のコンス トラクターを使用し、指定<xref:Microsoft.SqlServer.Management.Smo.DataType>オブジェクトのプロパティを明示的に  
  
-   オーバー ロードされたコンス トラクターを使用して、<xref:Microsoft.SqlServer.Management.Smo.DataType>プロパティをパラメーターとして。  
  
-   指定して、<xref:Microsoft.SqlServer.Management.Smo.DataType>インラインでオブジェクトのコンス トラクターです。  
  
-   静的メンバーのいずれかを使用して、<xref:Microsoft.SqlServer.Management.Smo.DataType>クラス、たとえば**Int**です。これによって、実際に <xref:Microsoft.SqlServer.Management.Smo.DataType> オブジェクトのインスタンスが返されます。  
  
 <xref:Microsoft.SqlServer.Management.Smo.DataType> オブジェクトには、データの型を定義するいくつかのプロパティがあります。 たとえば、<xref:Microsoft.SqlServer.Management.Smo.SqlDataType> プロパティは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型を指定します。 定数値を表す[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データ型が記載されて、<xref:Microsoft.SqlServer.Management.Smo.SqlDataType>列挙します。 これは、 **varchar**、 **nchar**、 **currency**、 **integer**、 **float**、および **datetime**などのデータ型を参照します。  
  
 データ型を確立したら、そのデータに対して特定のプロパティを設定する必要があります。 たとえば、 **nchar** 型の場合、 **Length** プロパティで文字列データの長さを設定する必要があります。 これは、有効桁数と小数点以下桁数を指定する必要のある数値に対しても同様です。  
  
 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> データ型および <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType> データ型は、ユーザーによって定義されるデータの型の定義を含んでいるオブジェクトを参照します。 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> は、<xref:Microsoft.SqlServer.Management.Smo.SqlDataType> 列挙からの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型に基づいています。 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>に基づく[!INCLUDE[msCoName](../../../includes/msconame-md.md)].NET データ型。 これらは、組織で定義されているビジネス ルールに従ってデータベースで頻繁に再利用される型のデータを表現していることが普通です。 たとえば、複数の通貨を扱う会社では、金額や通貨基準を格納するデータ型が役に立ちます。  
  
 <xref:Microsoft.SqlServer.Management.Smo.SqlDataType>列挙には、すべての一覧が含まれています、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-サポートされるデータ型。  
  
## <a name="examples"></a>使用例  
提供されているコード例を使用するには、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。 詳細については、次を参照してください[Visual C &#35; を作成する。Visual Studio .NET での SMO プロジェクト](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)です。  
  
  
## <a name="constructing-a-datatype-object-with-the-specification-in-the-constructor-in-visual-basic"></a>Visual Basic でのコンストラクター内の指定による DataType オブジェクトの構築  
 このコード例では、コンストラクターを使用して各種の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型に基づいたデータ型のインスタンスを作成する方法を示しています。  
  
> [!NOTE]  
>  <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>、<xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>、および XML 型にはすべて、オブジェクトを識別するための名前の値が必要です。  
  
```VBNET
'Declare a DataType object variable and define the data type in the constructor.
Dim dt As DataType
'For the decimal data type the following two arguements specify precision, and scale.
dt = New DataType(SqlDataType.Decimal, 10, 2)
``` 
  
## <a name="constructing-a-datatype-object-with-the-specification-in-the-constructor-in-visual-c"></a>Visual C# でのコンストラクター内の指定による DataType オブジェクトの構築  
 このコード例では、コンストラクターを使用して各種の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型に基づいたデータ型のインスタンスを作成する方法を示しています。  
  
> [!NOTE]  
>  <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>、<xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>、および XML 型にはすべて、オブジェクトを識別するための名前の値が必要です。  
  
```csharp  
{   
//Declare a DataType object variable and define the data type in the constructor.   
DataType dt;   
//For the decimal data type the following two arguements specify precision, and scale.   
dt = new DataType(SqlDataType.Decimal, 10, 2);   
}  
```  
  
## <a name="constructing-a-datatype-object-by-using-the-default-constructor-in-visual-basic"></a>Visual Basic での既定のコンストラクターを使用した DataType オブジェクトの構築  
 このコード例では、既定のコンストラクターを使用して各種の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型に基づいたデータ型のインスタンスを作成する方法を示します。 データ型の指定にはプロパティを使用します。  
  
 **注**、 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>、 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>、すべての XML 型がオブジェクトを識別する名前の値を必要とします。  
  
```VBNET
'Declare and create a DataType object variable.
Dim dt As DataType
dt = New DataType
'Define the data type by setting the SqlDataType property.
dt.SqlDataType = SqlDataType.VarChar
'The VarChar data type requires a value for the MaximumLength property.
dt.MaximumLength = 100
```
  
## <a name="constructing-a-datatype-object-by-using-the-default-constructor-in-visual-c"></a>Visual C# での既定のコンストラクターを使用した DataType オブジェクトの構築  
 このコード例では、既定のコンストラクターを使用して各種の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型に基づいたデータ型のインスタンスを作成する方法を示します。 データ型の指定にはプロパティを使用します。  
  
 **注**、 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>、 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>、すべての XML 型がオブジェクトを識別する名前の値を必要とします。  
  
```csharp  
{   
//Declare and create a DataType object variable.   
DataType dt;   
dt = new DataType();   
//Define the data type by setting the SqlDataType property.   
dt.SqlDataType = SqlDataType.VarChar;   
//The VarChar data type requires a value for the MaximumLength property.   
dt.MaximumLength = 100;   
}  
```  
  
  
