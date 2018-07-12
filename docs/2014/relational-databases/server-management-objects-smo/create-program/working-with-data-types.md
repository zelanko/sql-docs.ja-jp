---
title: データ型の使用 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- DataType object
- SQL Server Management Objects, data types
- data types [SMO]
- SMO [SQL Server], data types
ms.assetid: 1e0e736a-c709-4d89-aeb2-b32dcfd641fa
caps.latest.revision: 43
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 306b227a4b193811c7207f111fc35a48148e4bbf
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37228922"
---
# <a name="working-with-data-types"></a>データ型の処理
  データは、定義済みの長さを持つ文字列、特定の精度を持つ数値、または独自のルール セットを持つ別のオブジェクトであるユーザー定義データ型など、さまざまな型およびサイズで表現されます。 <xref:Microsoft.SqlServer.Management.Smo.DataType>によって適切に処理できるように、オブジェクトがデータの種類を分類[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。 <xref:Microsoft.SqlServer.Management.Smo.DataType> オブジェクトは、データを受け入れるオブジェクトに関連付けられています。 次[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]管理オブジェクト (SMO) オブジェクトに渡すデータによって定義する必要があります、<xref:Microsoft.SqlServer.Management.Smo.DataType>オブジェクトのプロパティ。  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Column>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunctionParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunctionParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedAggregateParameter>  
  
 データを受け入れるオブジェクトの `DataType` プロパティは、次のいくつかの方法で設定することができます。  
  
-   既定のコンス トラクターを使用し、指定<xref:Microsoft.SqlServer.Management.Smo.DataType>明示的にオブジェクトのプロパティ  
  
-   オーバー ロードされたコンス トラクターを使用して、<xref:Microsoft.SqlServer.Management.Smo.DataType>プロパティをパラメーターとして。  
  
-   指定、<xref:Microsoft.SqlServer.Management.Smo.DataType>オブジェクト コンス トラクターにインラインです。  
  
-   `Int` など、<xref:Microsoft.SqlServer.Management.Smo.DataType> クラスの静的メンバーの 1 つを使用する。 これによって、実際に <xref:Microsoft.SqlServer.Management.Smo.DataType> オブジェクトのインスタンスが返されます。  
  
 <xref:Microsoft.SqlServer.Management.Smo.DataType> オブジェクトには、データの型を定義するいくつかのプロパティがあります。 たとえば、<xref:Microsoft.SqlServer.Management.Smo.SqlDataType> プロパティは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型を指定します。 定数値を表す[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データ型が記載されて、<xref:Microsoft.SqlServer.Management.Smo.SqlDataType>列挙体。 これは、`varchar`、`nchar`、`currency`、`integer`、`float`、および `datetime` などのデータ型を参照します。  
  
 データ型を確立したら、そのデータに対して特定のプロパティを設定する必要があります。 たとえば、`nchar` 型の場合、`Length` プロパティで文字列データの長さを設定する必要があります。 これは、有効桁数と小数点以下桁数を指定する必要のある数値に対しても同様です。  
  
 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> データ型および <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType> データ型は、ユーザーによって定義されるデータの型の定義を含んでいるオブジェクトを参照します。 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> は、<xref:Microsoft.SqlServer.Management.Smo.SqlDataType> 列挙からの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型に基づいています。 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>に基づいて[!INCLUDE[msCoName](../../../includes/msconame-md.md)].NET データ型。 これらは、組織で定義されているビジネス ルールに従ってデータベースで頻繁に再利用される型のデータを表現していることが普通です。 たとえば、複数の通貨を扱う会社では、金額や通貨基準を格納するデータ型が役に立ちます。  
  
 <xref:Microsoft.SqlServer.Management.Smo.SqlDataType>列挙には、すべての一覧が含まれています、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-サポートされるデータ型。  
  
## <a name="examples"></a>使用例  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="constructing-a-datatype-object-with-the-specification-in-the-constructor-in-visual-basic"></a>Visual Basic でのコンストラクター内の指定による DataType オブジェクトの構築  
 このコード例は、コンス トラクターを使用して、別に基づくデータ型のインスタンスを作成する方法を示しています。[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データ型。  
  
> [!NOTE]  
>  <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>、<xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>、および XML 型にはすべて、オブジェクトを識別するための名前の値が必要です。  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDataTypes1](SMO How to#SMO_VBDataTypes1)]  -->  
  
## <a name="constructing-a-datatype-object-with-the-specification-in-the-constructor-in-visual-c"></a>Visual C# でのコンストラクター内の指定による DataType オブジェクトの構築  
 このコード例は、コンス トラクターを使用して、別に基づくデータ型のインスタンスを作成する方法を示しています。[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データ型。  
  
> [!NOTE]  
>  <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>、<xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>、および XML 型にはすべて、オブジェクトを識別するための名前の値が必要です。  
  
```  
{   
//Declare a DataType object variable and define the data type in the constructor.   
DataType dt;   
//For the decimal data type the following two arguements specify precision, and scale.   
dt = new DataType(SqlDataType.Decimal, 10, 2);   
}  
```  
  
## <a name="constructing-a-datatype-object-by-using-the-default-constructor-in-visual-basic"></a>Visual Basic での既定のコンストラクターを使用した DataType オブジェクトの構築  
 このコード例は、既定のコンス トラクターを使用して、別に基づくデータ型のインスタンスを作成する方法を示しています。[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データ型。 データ型の指定にはプロパティを使用します。  
  
 **注**、 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>、 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>、すべての XML 型のオブジェクトを識別する名前値は必要とします。  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDataTypes2](SMO How to#SMO_VBDataTypes2)]  -->  
  
## <a name="constructing-a-datatype-object-by-using-the-default-constructor-in-visual-c"></a>Visual C# での既定のコンストラクターを使用した DataType オブジェクトの構築  
 このコード例は、既定のコンス トラクターを使用して、別に基づくデータ型のインスタンスを作成する方法を示しています。[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データ型。 データ型の指定にはプロパティを使用します。  
  
 **注**、 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>、 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>、すべての XML 型のオブジェクトを識別する名前値は必要とします。  
  
```  
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
  
  
