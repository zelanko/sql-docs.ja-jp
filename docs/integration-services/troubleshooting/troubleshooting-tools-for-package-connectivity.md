---
title: "パッケージ接続のトラブルシューティング ツール | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SQL Server Integration Services パッケージ、トラブルシューティング"
  - "SSIS パッケージ、トラブルシューティング"
  - "Integration Services, トラブルシューティング"
  - "接続 [Integration Services], トラブルシューティング"
  - "エラー [Integration Services], トラブルシューティング"
  - "パッケージ [Integration Services]、トラブルシューティング"
ms.assetid: 08a019f5-8ba7-4527-97c1-e9846d4022ff
caps.latest.revision: 13
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 13
---
# パッケージ接続のトラブルシューティング ツール
[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] には、パッケージと、パッケージがデータを抽出して読み込むデータ ソースとの接続のトラブルシューティングを行うための、機能とツールが用意されています。  
  
## 外部データ プロバイダーの問題のトラブルシューティング  
 多くのパッケージが、外部データ プロバイダーとのやり取りで失敗します。 ところが、これらのプロバイダーが [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に返すメッセージには、多くの場合、トラブルシューティングを開始するための十分な情報が含まれていません。 トラブルシューティングのニーズに対応するために、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] では、パッケージと外部データ ソースとのやり取りに関するトラブルシューティングに使用できる新しいログ メッセージが採用されています。  
  
-   **ログ記録を有効にして、パッケージの Diagnostic イベントを選択すると、トラブルシューティング メッセージが表示されます**。 次に示す [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] コンポーネントは、すべての外部データ プロバイダーの呼び出しの前後に、メッセージをログに出力できます。  
  
    -   OLE DB 接続マネージャー、OLE DB ソース、および OLE DB 変換先  
  
    -   [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーおよび ADO NET 変換元  
  
    -   SQL 実行タスク  
  
    -   参照変換、OLE DB コマンド変換、および緩やかに変化するディメンション変換  
  
     ログ メッセージには、呼び出されるメソッドの名前が含まれています。 たとえば、これらのログ メッセージには OLE DB **Connection** オブジェクトの **Open** メソッド、または **Command** オブジェクトの **ExecuteNonQuery** メソッドが含まれています。 このメッセージの形式は次のとおりです。"%1!s!" は メソッド情報のプレースホルダーです。  
  
    ```  
    ExternalRequest_pre: The object is ready to make the following external request: '%1!s!'.  
    ExternalRequest_post: '%1!s!'. The external request has completed.  
    ```  
  
     外部データ プロバイダーとのやり取りに関するトラブルシューティングを行うには、ログを表示して、"前の" メッセージ (`ExternalRequest_pre`) に対応する "後の" メッセージがあるかどうかを確認します (`ExternalRequest_post`)。 対応する "後の" メッセージがない場合は、外部データ プロバイダーが予測どおりに応答しなかったことになります。  
  
     次の例では、これらのログ メッセージを含んでいるログの一部を示しています。  
  
    ```  
    ExternalRequest_pre: The object is ready to make the following external request: 'ITransactionJoin::JoinTransaction'.  
    ExternalRequest_post: 'ITransactionJoin::JoinTransaction succeeded'. The external request has completed.  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbConnection.Open'.  
    ExternalRequest_post: 'IDbConnection.Open succeeded'. The external request has completed.  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbConnection.CreateCommand'.  
    ExternalRequest_post: 'IDbConnection.CreateCommand finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbCommand.ExecuteReader'.  
    ExternalRequest_post: 'IDbCommand.ExecuteReader finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDataReader.GetSchemaTable'.  
    ExternalRequest_post: 'IDataReader.GetSchemaTable finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDataReader.Close'.  
    ExternalRequest_post: 'IDataReader.Close finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbConnection.Close'.  
    ExternalRequest_post: 'IDbConnection.Close finished'. The external request has completed."  
    ```  
  
## 参照  
 [パッケージ開発のトラブルシューティング ツール](../../integration-services/troubleshooting/troubleshooting-tools-for-package-development.md)   
 [パッケージ実行のトラブルシューティング ツール](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md)  
  
  