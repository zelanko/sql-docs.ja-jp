---
title: "セッション言語の設定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エラー [SQL Server]、国際化に関する注意点"
  - "グローバリゼーション [SQL Server]、セッション"
  - "時刻 [SQL Server]"
  - "セッション [SQL Server]、言語"
  - "国際化に関する注意点 [SQL Server]、セッション"
  - "日付 [SQL Server]、セッション言語"
  - "国際化に関する注意点 [SQL Server]、セッション"
  - "クライアント側セッション言語"
  - "時刻 [SQL Server]、セッション言語"
  - "メッセージ [SQL Server]、国際化に関する注意点"
  - "クライアント側セッション言語"
ms.assetid: de7f2c90-8f4f-4cfc-94cc-4933a7fd2bde
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# セッション言語の設定
  セッション言語は、言語とカルチャの設定に基づいて、次の要素がサーバー上でどのように表示されるかを設定するために使用できます。  
  
-   エラーとその他のシステム メッセージで使用される言語。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が使用できるすべての言語で、すべてのシステム エラー文字列とシステム メッセージの複数のコピーを保持できます。 このようなメッセージは、[sys.messages](../Topic/sys.messages%20\(Transact-SQL\).md) カタログ ビューに表示できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカライズ版をインストールすると、これらのシステム メッセージが、インストールする言語バージョン用に変換されます。 既定では、これらのメッセージの英語 (U.S.) セットも取得されます。 さらに、[sp_addmessage](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md) を使用して、特定の言語のユーザー定義メッセージを追加することもできます。  
  
-   日付と時刻のデータの形式  
  
-   略記を含む、曜日と月の名前  
  
-   週の最初の曜日  
  
-   通貨データ  
  
 セッション設定として 33 種類の言語を使用できます。 言語の一覧については、「[sys.syslanguages](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)」を参照してください。  
  
## サーバーからのセッション言語の設定  
 セッション言語をサーバー側から設定するには、[SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md) を使用します。  
  
## クライアントからのセッション言語の設定  
 セッション言語は、OLE DB、ODBC、または ADO.NET を使用してクライアント側で設定できます。 OLE DB の場合は、SSPROP_INIT_CURRENTLANGUAGE プロパティを使用します。 詳細については、「「[初期化プロパティと承認プロパティ](../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md)」を参照してください。  
  
 ODBC の場合は、Language キーワードを使用します。 詳細については、「[SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md)」を参照してください。  
  
 ADO.NET の場合は、**ConnectionString** オブジェクトの **Current Language** パラメーターを使用します。 詳細については、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Data Access Components (MDAC) ソフトウェア開発キット (SDK) のドキュメントを参照してください。  
  
  