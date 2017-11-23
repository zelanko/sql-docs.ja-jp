---
title: "SQLXML マネージ クラス |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
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
caps.latest.revision: "25"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0f2d79aae0c863030a478ed2e3859785d491be61
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sqlxml-40-net-framework-support---managed-classes"></a>SQLXML 4.0 の .NET Framework のサポート、マネージ クラス
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)][!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 のインスタンスから XML データにアクセスするアプリケーションを作成できるようにする機能をサポートしている[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、データを取り込み、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework 環境、プロセス データおよびに送信[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. 
  
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML マネージ クラスでは、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework 内で SQLXML 4.0 の機能へのアクセスが提供されます。 SQLXML マネージ クラスを使用すると、C# アプリケーションを作成して、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスから XML データにアクセスしたり、.NET Framework 環境にデータを取り込んだり、データを処理したり、変更を DiffGram として [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に送信し適用することができます。 SQL マネージ クラスを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースに更新を適用するときには、マッピング スキーマを使用する必要があります。 作業用サンプルについては、次を参照してください。 [.NET 環境での SQLXML 機能へのアクセス](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/accessing-sqlxml-functionality-in-the-net-environment.md)です。  
  
 SQLXML 4.0 で SQLXML マネージ クラスを使用するには、Microsoft Visual Studio をインストールする必要があります。  
  
> [!NOTE]  
>  .NET Framework には [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .NET データ プロバイダーが含まれています。 このプロバイダーは .NET 環境から [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] へのアクセスに使用できますが、扱えるのは従来の SQL クエリ (FOR XML クエリ以外のリレーショナル データベース クエリ) だけです。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で XML テンプレートやサーバー側の XPath クエリを実行することはできません。  

 アクセスして、データの変更については[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]内で、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework、およびデータを更新する Diffgram を使用した[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、テーブルを参照してください[.NET環境でのSQLXML機能へのアクセス](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/accessing-sqlxml-functionality-in-the-net-environment.md).  
  
> [!NOTE]  
>  XML 一括読み込みを使用して XML ドキュメントの一括読み込みを行う [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio アプリケーションを作成することもできます。 詳細については、次を参照してください。 [XML データの一括読み込みを実行する &#40;です。SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md). 作成するアプリケーションには、XML 一括読み込みの DLL (Xblkld4.dll) への参照を追加する必要があります。 これは COM DLL で、Visual Studio .NET ではこのラッパー ライブラリが自動的に作成されます。  
  
  このセクションで説明を使用する方法を示すサンプル アプリケーション、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML マネージ クラス。  
 [実行中の SQL クエリ &#40;です。SQLXML マネージ クラス&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-sql-queries-sqlxml-managed-classes.md)  
  [ExecuteXMLReader メソッドを使用した SQL クエリの実行](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-sql-queries-by-using-the-executexmlreader-method.md)  
  [クライアント側 &#40; XML の処理SQLXML マネージ クラス&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/processing-xml-on-the-client-side-sqlxml-managed-classes.md)  
  [実行中の XPath クエリ &#40;です。SQLXML マネージ クラス&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-xpath-queries-sqlxml-managed-classes.md)  
  [名前空間 &#40; での XPath クエリの実行SQLXML マネージ クラス&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-xpath-queries-with-namespaces-sqlxml-managed-classes.md)  
  [CommandText プロパティを使用したテンプレート ファイルの実行](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-template-files-by-using-the-commandtext-property.md)  
  [CommandStream プロパティを使用したテンプレート ファイルの実行](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-template-files-by-using-the-commandstream-property.md)  
  [XSL 変換 &#40; を適用します。SQLXML マネージ クラス&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/applying-an-xsl-transformation-sqlxml-managed-classes.md)  
  

  
  
