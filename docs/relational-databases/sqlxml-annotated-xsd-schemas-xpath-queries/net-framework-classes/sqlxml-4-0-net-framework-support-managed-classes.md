---
title: SQLXML マネージ クラス |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- .NET Framework [SQLXML], Managed Classes
- SQL Server .NET Data Provider
- Managed Classes [SQLXML], about managed classes
- providers [SQLXML], SQL Server .NET Data Provider
- data providers [SQLXML], SQL Server .NET Data Provider
- Managed Classes [SQLXML]
- XML [SQLXML]
- SQLXML Managed Classes
- providers [SQLXML], SQLXML Managed Classes
- data providers [SQLXML], SQLXML Managed Classes
- SQLXML, Managed Classes
ms.assetid: 73a5faeb-dabf-4895-acb5-a9651b646065
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 562b75d19715c0cf52cf8eeaf499f142a2b27080
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68119608"
---
# <a name="sqlxml-40-net-framework-support---managed-classes"></a>SQLXML 4.0 の .NET Framework サポート - マネージド クラス
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 では、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスから XML データへのアクセス、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework 環境へのデータの移動、データの処理、および [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] への更新の適用を行うアプリケーションを作成するための機能がサポートされています。 
  
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML マネージド クラスでは、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework 内で SQLXML 4.0 の機能へのアクセスが提供されます。 SQLXML マネージド クラスを使用すると、C# アプリケーションを作成して、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスから XML データにアクセスしたり、.NET Framework 環境にデータを取り込んだり、データを処理したり、変更を DiffGram として [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に送信し適用することができます。 SQL マネージド クラスを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースに更新を適用するときには、マッピング スキーマを使用する必要があります。 実際のサンプルでは、次を参照してください。 [.NET 環境での SQLXML 機能へのアクセス](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/accessing-sqlxml-functionality-in-the-net-environment.md)します。  
  
 SQLXML 4.0 で SQLXML マネージド クラスを使用するには、Microsoft Visual Studio をインストールする必要があります。  
  
> [!NOTE]  
>  .NET Framework には [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .NET データ プロバイダーが含まれています。 このプロバイダーは .NET 環境から [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] へのアクセスに使用できますが、扱えるのは従来の SQL クエリ (FOR XML クエリ以外のリレーショナル データベース クエリ) だけです。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で XML テンプレートやサーバー側の XPath クエリを実行することはできません。  

 アクセスして、データの変更について[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]内、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework、およびデータを更新する Diffgram を使用[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]テーブルを参照してください[.NET環境でのSQLXML機能へのアクセス](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/accessing-sqlxml-functionality-in-the-net-environment.md).  
  
> [!NOTE]  
>  XML 一括読み込みを使用して XML ドキュメントの一括読み込みを行う [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio アプリケーションを作成することもできます。 詳細については、次を参照してください。 [XML データの一括読み込みを実行する&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)します。 作成するアプリケーションには、XML 一括読み込みの DLL (Xblkld4.dll) への参照を追加する必要があります。 これは COM DLL で、Visual Studio .NET ではこのラッパー ライブラリが自動的に作成されます。  
  
  このセクションを使用する方法を示すサンプル アプリケーションを提供する、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML マネージ クラス。  
 [SQL クエリの実行&#40;SQLXML マネージ クラス&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-sql-queries-sqlxml-managed-classes.md)  
  [ExecuteXMLReader メソッドを使用した SQL クエリの実行](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-sql-queries-by-using-the-executexmlreader-method.md)  
  [クライアント側の XML 処理&#40;SQLXML マネージ クラス&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/processing-xml-on-the-client-side-sqlxml-managed-classes.md)  
  [XPath クエリの実行&#40;SQLXML マネージ クラス&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-xpath-queries-sqlxml-managed-classes.md)  
  [XPath クエリの名前空間を持つ実行&#40;SQLXML マネージ クラス&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-xpath-queries-with-namespaces-sqlxml-managed-classes.md)  
  [CommandText プロパティを使用したテンプレート ファイルの実行](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-template-files-by-using-the-commandtext-property.md)  
  [CommandStream プロパティを使用したテンプレート ファイルの実行](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-template-files-by-using-the-commandstream-property.md)  
  [XSL 変換の適用&#40;SQLXML マネージ クラス&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/applying-an-xsl-transformation-sqlxml-managed-classes.md)  
  

  
  
