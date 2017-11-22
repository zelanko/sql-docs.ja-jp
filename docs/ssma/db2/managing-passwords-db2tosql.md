---
title: "パスワード (DB2ToSQL) を管理する |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 56d546e3-8747-4169-aace-693302667e94
caps.latest.revision: "5"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0e6ee12eb7a0d75c503906046e05cef4d61180d7
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="managing-passwords-db2tosql"></a>パスワード (DB2ToSQL) を管理します。
このセクションでは、データベースのパスワードとをインポートまたはサーバー間でそれらをエクスポートする手順のセキュリティ保護については。  
  
1.  パスワードをセキュリティで保護します。  
  
2.  エクスポートまたは暗号化されたパスワードをインポートします。  
  
## <a name="securing-password"></a>パスワードをセキュリティで保護します。  
SSMA では、データベースのパスワードをセキュリティで保護することができます。  
  
セキュリティで保護された接続を実装するのにには、次の手順を使用します。  
  
次の 3 つのメソッドのいずれかを使用して、有効なパスワードを指定します。  
  
1.  **クリア テキスト:** 'password' のノードの value 属性に、データベースのパスワードを入力します。 スクリプト ファイルまたはサーバー接続ファイルの [サーバー] セクションで、サーバーの定義ノードがあります。  
  
    パスワードがクリア テキストでは、安全ではありません。 そのため、コンソール出力には、次の警告メッセージが発生: *"サーバー&lt;サーバー id&gt;パスワードが SSMA コンソール アプリケーションが暗号化によるパスワードの保護、詳細についてはヘルプ ファイルを SSMA で – securepassword オプションを参照してくださいするオプションを提供するクリア テキストのセキュリティ保護されていない形式で指定します"。*  
  
    **暗号化されたパスワードは、**この場合、指定したパスワードが ProtectedStorage.ssma でローカル コンピューター上の暗号化された形式で保存はできます。  
  
    -   **パスワードのセキュリティ保護**  
  
        -   実行、`SSMAforDB2Console.exe`で、`–securepassword`しサーバーの定義 セクションで パスワード ノードを含む接続またはスクリプト ファイルをサーバーに渡すコマンド ライン スイッチを追加します。  
  
        -   プロンプトで、ユーザーは、データベースのパスワードを入力し、確認を求められます。  
  
            サーバー定義 id とその対応する暗号化されたパスワードがローカル コンピューター上のファイルに格納されています。  
            
            例 1 : 
            
                Specify password
                C:\SSMA\SSMAforDB2Console.EXE –securepassword –add all –s "D:\Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts\AssessmentReportGenerationSample.xml" –v "D:\Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts\ VariableValueFileSample.xml"
                
                Enter password for server_id 'XXX_1': xxxxxxx
                
                Re-enter password for server_id 'XXX_1': xxxxxxx
            
            例 2:
            
                C:\SSMA\SSMAforDB2Console.EXE –securepassword –add "source_1,target_1" –c "D:\Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts\ServersConnectionFileSample.xml" – v "D:\Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts\ VariableValueFileSample.xml" -o
                
                Enter password for server_id 'source_1': xxxxxxx
                
                Re-enter password for server_id 'source_1': xxxxxxx
                
                Enter password for server_id 'target_1': xxxxxxx
                
                Re-enter password for server_id 'target _1': xxxxxxx  
    
    -   **暗号化されたパスワードを削除します。**  
  
        実行、`SSMAforDB2Console.exe`で、`–securepassword`と`–remove`コマンドラインはローカル コンピューターに存在する保護されたストレージ ファイルから暗号化されたパスワードを削除する、サーバー id を渡すことで切り替えます。  
  
        例:  
        
            C:\SSMA\SSMAforDB2Console.EXE –securepassword –remove all
            C:\SSMA\SSMAforDB2Console.EXE –securepassword –remove "source_1,target_1"  
  
    -   **暗号化パスワードを持つサーバー Id の一覧表示**  
  
        実行、`SSMAforDB2Console.exe`で、`–securepassword`と`–list`パスワードが暗号化されているすべてのサーバー id を一覧表示するコマンド ライン スイッチです。  
  
        例:  
        
            C:\SSMA\SSMAforDB2Console.EXE –securepassword –list  

  
    > [!NOTE]  
    > 1.  スクリプトまたはサーバーの接続ファイルに示されているクリア テキストでパスワードは、セキュリティで保護されたファイルの暗号化されたパスワードよりも優先されます。  
    > 2.  サーバー接続のファイルまたはスクリプト ファイルの [サーバー] セクションではパスワードが存在しない場合、またはローカル コンピューターのセキュリティ保護されていないが場合は、コンソールでは、パスワードを入力するように求められます。  
  
## <a name="exporting-or-importing-encrypted-passwords"></a>エクスポートまたは暗号化されたパスワードをインポートします。  
SSMA コンソール アプリケーションでは、暗号化されたデータベースのパスワードがローカル コンピューター上のファイルに存在をセキュリティで保護されたファイルおよびその逆にエクスポートできます。 独立した暗号化されたパスワードのマシンの作成に役立ちます。 エクスポート機能 id を読み取り、サーバーと、ローカルのパスワードが記憶域が保護されているし、暗号化されたファイルに情報を保存します。 セキュリティで保護されたファイルのパスワードの入力を求められます。 入力したパスワードは 8 文字の長さ以上を確認します。 このセキュリティで保護されたファイルは、異なるコンピューター間で移植します。 インポート機能は、セキュリティで保護されたファイルからの id とパスワード情報をサーバーに読み取ります。 ユーザーは、セキュリティで保護されたファイルのパスワードを入力するように要求し、ローカルの保護された記憶域の末尾に追加します。  
  
例:  

    Export password
    
    Enter password for protecting the exported file
    
    C:\SSMA\SSMAforDB2Console.EXE –securepassword –export all "machine1passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforDB2Console.EXE –p –e "DB2DB_1_1,Sql_1" "machine2passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  
  
例:  

    Import an encrypted password
    
    Enter password for protecting the imported file
    
    C:\SSMA\SSMAforDB2Console.EXE –securepassword –import all "machine1passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforDB2Console.EXE –p –i "DB2DB_1,Sql_1" "machine2passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx

  
## <a name="see-also"></a>参照  
[SSMA コンソールの実行](http://msdn.microsoft.com/en-us/ce63f633-067d-4f04-b8e9-e1abd7ec740b)  
  
