---
title: "その他の SQL Server 以外のサブスクライバー | Microsoft Docs"
ms.custom: ""
ms.date: "03/08/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SQL Server 以外のサブスクライバー, 他の種類"
ms.assetid: 96b8beb9-38e8-4ce4-97ca-c0f8656b73b4
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 31
---
# その他の SQL Server 以外のサブスクライバー
  以外の一覧については[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] でサポートされているサブスクライバー [!INCLUDE[msCoName](../../../includes/msconame-md.md)], を参照してください [非 SQL Server サブスクライバー](../../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)します。 ここでは、ODBC ドライバーと OLE DB プロバイダーの要件について説明します。  
  
## ODBC ドライバーの要件  
 ODBC ドライバーは、以下の要件を満たす必要があります。  
  
-   ODBC Level-1 に準拠している  
  
-   スレッド セーフのディストリビューター環境である  
  
-   トランザクションの実行が可能である  
  
-   データ定義言語 (DDL) をサポートする  
  
-   読み取り専用にはできない  
  
-   など、長いテーブル名をサポートする必要があります **MSreplication_subscriptions**します。  
  
## OLE DB インターフェイスを使用するレプリケーション  
 トランザクション レプリケーションを行うには、OLE DB プロバイダーが以下のオブジェクトをサポートする必要があります。  
  
-   **データ ソース** オブジェクト  
  
-   **セッション** オブジェクト  
  
-   **コマンド** オブジェクト  
  
-   **行セット** オブジェクト  
  
-   **エラー** オブジェクト  
  
### DataSource オブジェクト インターフェイス  
 データ ソースに接続するためには、以下のインターフェイスが必要です。  
  
-   **IDBInitialize**  
  
-   **IDBCreateSession**  
  
-   **IDBProperties**  
  
 プロバイダーがサポートされている場合、 **IDBInfo** インターフェイス、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 引用符で囲まれた識別子の文字、SQL ステートメントの最大長、およびテーブルおよび列名の文字の最大数などの情報を取得するインターフェイスを使用します。  
  
### Session オブジェクト インターフェイス  
 以下のインターフェイスが必要です。  
  
-   **IDBCreateCommand**  
  
-   **ITransaction**  
  
-   **ITransactionLocal**  
  
-   **IDBSchemaRowset**  
  
### Command オブジェクト インターフェイス  
 以下のインターフェイスが必要です。  
  
-   **ICommand**  
  
-   **ICommandProperties**  
  
-   **ICommandText**  
  
-   **ICommandPrepare**  
  
-   **IColumnsInfo**  
  
-   **IAccessor**  
  
-   **ICommandWithParameters**  
  
 **IAccessor** パラメーター アクセサーを作成する必要があります。 プロバイダーがサポートされている場合 **IColumnRowset**, 、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] そのインターフェイスを使用して、列が id 列であるかどうかを確認します。  
  
### Rowset オブジェクト インターフェイス  
 以下のインターフェイスが必要です。  
  
-   **IRowset**  
  
-   **IAccessor**  
  
-   **IColumnsInfo**  
  
 アプリケーションは、サブスクリプション データベース内に作成された、レプリケートされるテーブル上の行セットを開く必要があります。 **IColumnsInfo** と **IAccessor** 行セット内のデータにアクセスするために必要なです。  
  
### Error オブジェクト インターフェイス  
 エラーの管理には、以下のインターフェイスを使用します。  
  
-   **IErrorRecords**  
  
-   **IErrorInfo**  
  
 使用 **ISQLErrorInfo** OLE DB プロバイダーによってサポートされている場合。  
  
 OLE DB プロバイダーの詳細については、OLE DB プロバイダー付属のマニュアルを参照してください。  
  
## 参照  
 [SQL Server 以外のサブスクライバー](../../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)  
  
  