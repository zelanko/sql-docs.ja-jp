---
title: パスワード (DB2ToSQL) の管理 |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 56d546e3-8747-4169-aace-693302667e94
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 2a2ba7cfb16c4df96fa40edb23d9bccea3599005
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51675658"
---
# <a name="managing-passwords-db2tosql"></a>パスワードの管理 (DB2ToSQL)
このセクションでは、データベースのパスワードとサーバー間でのエクスポートをインポートまたはプロシージャのセキュリティ保護の詳細については。  
  
1.  パスワードをセキュリティで保護します。  
  
2.  エクスポートまたは暗号化されたパスワードをインポートします。  
  
## <a name="securing-password"></a>パスワードをセキュリティで保護します。  
SSMA では、データベースのパスワードをセキュリティで保護できます。  
  
セキュリティで保護された接続を実装するために、次の手順を使用します。  
  
次の 3 つのメソッドのいずれかを使用して有効なパスワードを指定します。  
  
1.  **クリア テキスト:** 'password' ノードの値の属性に、データベースのパスワードを入力します。 これはスクリプト ファイルまたはサーバー接続ファイルの [サーバー] セクションで、サーバーの定義のノードの下にあります。  
  
    パスワードがクリア テキストでは、安全ではありません。 そのため、コンソール出力には、次の警告メッセージが発生: *"Server&lt;サーバー id&gt;パスワードはクリア テキストの安全でないフォームでは、SSMA コンソール アプリケーションは保護するオプションを提供します、暗号化を使用してパスワードを参照してください SSMA で – securepassword オプションの詳細についてはヘルプ ファイル。"*  
  
    **暗号化されたパスワードは、** この場合、指定したパスワードが ProtectedStorage.ssma でローカル コンピューターの暗号化された形式で格納されます。  
  
    -   **パスワードをセキュリティで保護します。**  
  
        -   実行、`SSMAforDB2Console.exe`で、`–securepassword`サーバー定義のセクションではパスワード ノードを含む接続またはスクリプト ファイルをサーバーに渡すコマンド ライン スイッチを追加します。  
  
        -   プロンプトで、ユーザーは、データベースのパスワードを入力し、確認を求められます。  
  
            サーバーの定義 id とその対応する暗号化されたパスワードがローカル コンピューター上のファイルに格納されています。  
            
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
  
        実行、`SSMAforDB2Console.exe`で、`–securepassword`と`–remove`で暗号化されたパスワードをローカル コンピューターに存在する保護されたストレージ ファイルから削除する、サーバー id を渡すコマンド ライン スイッチします。  
  
        例:  
        
            C:\SSMA\SSMAforDB2Console.EXE –securepassword –remove all
            C:\SSMA\SSMAforDB2Console.EXE –securepassword –remove "source_1,target_1"  
  
    -   **パスワードが暗号化されてサーバー Id の一覧表示**  
  
        実行、`SSMAforDB2Console.exe`で、`–securepassword`と`–list`コマンドラインでパスワードが暗号化されているすべてのサーバー id を一覧表示するために切り替えます。  
  
        例:  
        
            C:\SSMA\SSMAforDB2Console.EXE –securepassword –list  

  
    > [!NOTE]  
    > 1.  スクリプトまたはサーバーの接続ファイルで説明したクリア テキストでパスワードは、セキュリティで保護されたファイル内の暗号化されたパスワードよりも優先されます。  
    > 2.  サーバー接続ファイルまたはスクリプト ファイルの [サーバー] セクションではパスワードが存在しない場合、またはローカル コンピューターのセキュリティ保護されていないが場合は、コンソールでは、パスワードを入力するように求められます。  
  
## <a name="exporting-or-importing-encrypted-passwords"></a>エクスポートまたは暗号化されたパスワードをインポートします。  
SSMA コンソール アプリケーションをセキュリティで保護されたファイル、およびその逆に、ローカル コンピューター上のファイルに存在するデータベースの暗号化されたパスワードをエクスポートすることができます。 暗号化されたパスワードのマシンを独立したために役立ちます。 エクスポート機能は、サーバー id を読み取ると、ローカル コンピューターからパスワード保護された記憶域と、暗号化されたファイルに情報を保存します。 セキュリティで保護されたファイルのパスワードの入力を求められます。 入力したパスワードは 8 文字の長さ以上を確認します。 このセキュリティで保護されたファイルは、別のコンピューター間で可能です。 インポート機能では、セキュリティで保護されたファイルから、サーバー id とパスワードの情報を読み取ります。 ユーザーはセキュリティで保護されたファイルのパスワードを入力するように求められ、保護されているローカル ストレージに情報を追加します。  
  
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
[SSMA コンソールの実行](https://msdn.microsoft.com/ce63f633-067d-4f04-b8e9-e1abd7ec740b)  
  
