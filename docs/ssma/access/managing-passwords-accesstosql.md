---
title: パスワードの管理 (管理用 Sql) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: b099d0f9-dd37-4c87-8b6f-ed0177881ea4
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 5d8886f28a30f264e0357af82724567e42e3bd5a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67907184"
---
# <a name="managing-passwords-accesstosql"></a>パスワードの管理 (管理用 Sql)
このセクションでは、データベースのパスワードをセキュリティで保護する方法と、サーバー間でインポートまたはエクスポートする手順について説明します。  
  
1.  パスワードのセキュリティ保護  
  
2.  暗号化されたパスワードのエクスポートまたはインポート  
  
## <a name="securing-password"></a>パスワードのセキュリティ保護  
SSMA を使用すると、データベースのパスワードをセキュリティで保護することができます。  
  
セキュリティで保護された接続を実装するには、次の手順に従います。  
  
次の3つの方法のいずれかを使用して、有効なパスワードを指定します。  
  
1.  **クリアテキスト:**[パスワード] ノードの値属性にデータベースパスワードを入力します。 これは、スクリプトファイルまたはサーバー接続ファイルのサーバーセクションの [サーバー定義] ノードの下にあります。  
  
    クリアテキストのパスワードはセキュリティで保護されていません。 このため、コンソールの出力には、 *"サーバー &lt;サーバー-&gt; id パスワードはセキュリティで保護されていないクリアテキスト形式で提供されます。 ssma コンソールアプリケーションは、暗号化によってパスワードを保護するオプションを提供します。詳細については、ssma ヘルプファイルの-securepassword オプションを参照してください。"*  
  
    **暗号化されたパスワード:** この場合、指定されたパスワードは、ProtectedStorage のローカルコンピューター上の暗号化された形式で格納されます。  
  
    -   **パスワードのセキュリティ保護**  
  
        -   `-securepassword`を`SSMAforAccessConsole.exe`使用してを実行し、コマンドラインで [サーバーの定義] セクションの [パスワード] ノードを含むサーバー接続またはスクリプトファイルを渡します。  
  
        -   プロンプトが表示されたら、データベースのパスワードを入力して確認します。  
  
            サーバー定義 id とそれに対応する暗号化されたパスワードは、ローカルコンピューター上のファイルに格納されます。  
  
            例 1:
            
                Specify password
                
                C:\SSMA\SSMAforAccessConsole.EXE -securepassword -add all -s "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\AssessmentReportGenerationSample.xml" -v "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ VariableValueFileSample.xml"
                
                Enter password for server_id 'XXX_1': xxxxxxx
                
                Re-enter password for server_id 'XXX_1': xxxxxxx  
            
            例 2:
            
                C:\SSMA\SSMAforAccessConsole.EXE -securepassword -add "source_1,target_1" -c "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ServersConnectionFileSample.xml" - v "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ VariableValueFileSample.xml" -o
                
                Enter password for server_id 'source_1': xxxxxxx
                
                Re-enter password for server_id 'source_1': xxxxxxx
                
                Enter password for server_id 'target_1': xxxxxxx
                
                Re-enter password for server_id 'target _1': xxxxxxx  
  
    -   **暗号化されたパスワードの削除**  
  
        とを`SSMAforAccessConsole.exe`使用して`-remove`を実行し、サーバー id を渡してコマンドラインでを実行して、暗号化されたパスワードをローカルコンピューターに存在する保護されたストレージファイルから削除します。`-securepassword`  
  
            C:\SSMA\SSMAforAccessConsole.EXE -securepassword -remove all
            C:\SSMA\SSMAforAccessConsole.EXE -securepassword -remove "source_1,target_1"  
  
    -   **パスワードが暗号化されているサーバー Id を一覧表示する**  
  
        `-securepassword`と`-list`スイッチを使用してコマンドラインで SSMAforAccessConsole を実行し、パスワードが暗号化されているすべてのサーバー id を一覧表示します。  
  
            C:\SSMA\SSMAforAccessConsole.EXE -securepassword -list  
  
    > [!NOTE]  
    > 1.  スクリプトまたはサーバー接続ファイルで説明されているクリアテキストのパスワードは、セキュリティで保護されたファイルの暗号化されたパスワードよりも優先されます。  
    > 2.  サーバー接続ファイルまたはスクリプトファイルの server セクションにパスワードが存在しない場合、またはローカルコンピューター上でセキュリティ保護されていない場合は、コンソールにパスワードの入力を求めるメッセージが表示されます。  
  
## <a name="exporting-or-importing-encrypted-passwords"></a>暗号化されたパスワードのエクスポートまたはインポート  
SSMA コンソールアプリケーションを使用すると、ローカルコンピューター上のファイルに存在する暗号化されたデータベースパスワードを、セキュリティで保護されたファイルにエクスポートできます。また、その逆も可能です。 暗号化されたパスワードをコンピューターに依存させるのに役立ちます。 エクスポート機能は、ローカルで保護されているストレージからサーバー id とパスワードを読み取り、暗号化されたファイルに情報を保存します。 ユーザーは、セキュリティで保護されたファイルのパスワードを入力するように求められます。 入力したパスワードの長さが8文字以上であることを確認します。 このセキュリティで保護されたファイルは、異なるコンピューター間で移植できます。 インポート機能は、サーバー id とパスワードの情報をセキュリティで保護されたファイルから読み取ります。 ユーザーは、セキュリティで保護されたファイルのパスワードを入力するように求められ、ローカルで保護されているストレージに情報が追加されます。  


    Export password
    
    Enter password for protecting the exported file
    
    C:\SSMA\SSMAforAccessConsole.EXE -securepassword -export all "machine1passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforAccessConsole.EXE -p -e "AccessDB_1_1,Sql_1" "machine2passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  


    Import an encrypted password
    
    Enter password for protecting the imported file
    
    C:\SSMA\SSMAforAccessConsole.EXE -securepassword -import all "machine1passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforAccessConsole.EXE -p -i "AccessDB_1,Sql_1" "machine2passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  
  
## <a name="see-also"></a>参照  
[SSMA コンソール (アクセス) の実行](https://msdn.microsoft.com/aa1bf665-8dc0-4259-b36f-46ae67197a43)  
  
