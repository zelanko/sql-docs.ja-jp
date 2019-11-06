---
title: SQLXMLOLEDB プロバイダーの使用 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sample applications [SQLXML]
- SQLXMLOLEDB Provider, samples
- ClientSideXML property
ms.assetid: fbcefac5-29c9-478b-b0e0-d510b593f446
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9bc5e79f52f3aabbe157065db86e8d0968537ef7
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2019
ms.locfileid: "72909353"
---
# <a name="using-the-sqlxmloledb-provider-sqlxml-40"></a>SQLXMLOLEDB プロバイダーの使用 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  ここでは、SQLXMLOLEDB プロバイダー固有のプロパティの使用法を示す ADO サンプル アプリケーションを紹介します。  
  
## <a name="application-requirements-for-sqlxmloledb-40-provider"></a>SQLXMLOLEDB 4.0 プロバイダーのアプリケーション要件  
 SQLXMLOLEDB 4.0 を使用する実際のサンプルを作成するには、次の作業が必要です。  
  
1.  Microsoft Visual Basic の .exe アプリケーションを作成し、次のいずれかの参照を追加します。  
  
    -   Microsoft ActiveX データオブジェクト2.6 ライブラリ  
  
    -   Microsoft ActiveX データオブジェクト2.7 ライブラリ  
  
    -   Microsoft ActiveX Data Objects 2.8 Library  
  
2.  SQLXML 4.0 と [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client を配置し、インストールします。  

     詳細については、「 [SQLXML 4.0 のプログラミング概念](../../../relational-databases/sqlxml/sqlxml-4-0-programming-concepts.md)」および「 [SQL Server Native Client のインストール](../../../relational-databases/native-client/applications/installing-sql-server-native-client.md)」を参照してください。  
  
## <a name="in-this-section"></a>トピックの内容  
 [SQL クエリ&#40;の実行 SQLXMLOLEDB プロバイダー&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-sql-queries-sqlxmloledb-provider.md)  
 ClientSideXML および xml ルートプロパティを使用して SQL クエリを実行する方法について説明します。  
  
 [SQL クエリ&#40;を含むテンプレートの実行 SQLXMLOLEDB プロバイダー&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-templates-that-contain-sql-queries-sqlxmloledb-provider.md)  
 ClientSideXML プロパティの使用方法を示します。  
  
 [XPath クエリ&#40;の実行 SQLXMLOLEDB プロバイダー&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-xpath-queries-sqlxmloledb-provider.md)  
 ClientSideXML、基本パス、およびマッピングスキーマプロパティの使用方法を示します。  
  
 [名前空間&#40;SQLXMLOLEDB プロバイダーを使用した XPath クエリの実行&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-xpath-queries-with-namespaces-sqlxmloledb-provider.md)  
 名前空間の修飾子が付けられたスキーマに対してクエリを実行する方法を示します。  
  
 [XPath クエリ&#40;を含むテンプレートの実行 SQLXMLOLEDB プロバイダー&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-templates-that-contain-xpath-queries-sqlxmloledb-provider.md)  
 ClientSideXML、ベースパス、およびマッピングスキーマプロパティを使用して、SQL クエリでテンプレートを実行する方法について説明します。  
  
 [XSL Transformation &#40;SQLXMLOLEDB プロバイダーの適用&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/applying-an-xsl-transformation-sqlxmloledb-provider.md)  
 XSL 変換の適用時に ClientSideXML プロパティと xsl プロパティを使用する方法を示します。  
  
## <a name="see-also"></a>「  
 [SQL Server Native Client のシステム要件](../../../relational-databases/native-client/system-requirements-for-sql-server-native-client.md)  
  
  
