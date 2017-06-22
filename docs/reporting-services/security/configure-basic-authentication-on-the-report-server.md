---
title: "レポート サーバーで基本認証を構成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/26/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Reporting Services, configuration
- Basic authentication
ms.assetid: 8faf2938-b71b-4e61-a172-46da2209ff55
caps.latest.revision: 28
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: bfadbdb617198fe04b789d0d1d6589f4af2d887f
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="configure-basic-authentication-on-the-report-server"></a>レポート サーバーで基本認証を構成する
  Reporting Services は、既定では、ネゴシエート認証および NTLM 認証を指定する要求を受け入れます。 基本認証を使用するクライアント アプリケーションやブラウザーが配置に含まれる場合は、サポートされる種類の一覧に基本認証を追加する必要があります。 また、レポート ビルダーを使用する場合は、レポート ビルダーのファイルへの匿名アクセスを有効にする必要もあります。  
  
 レポート サーバーで基本認証を構成するには、RSReportServer.config ファイルの XML 要素と値を編集する必要があります。 既定値を置き換える際に、このトピックの例をコピーして貼り付けることもできます。  
  
 基本認証を有効にする前に、セキュリティ インフラストラクチャで基本認証がサポートされていることを確認します。 基本認証では、レポート サーバー Web サービスがローカル セキュリティ機関に資格情報を渡します。 資格情報でローカル ユーザー アカウントが指定されていた場合は、ユーザーはレポート サーバー コンピューター上のローカル セキュリティ機関によって認証されて、ローカル リソースに対して有効なセキュリティ トークンを受け取ります。 ドメイン ユーザー アカウントの資格情報は、ドメイン コントローラーに転送されて認証されます。 この場合は、認証が完了すると、ネットワーク リソースに対して有効なチケットが渡されます。  
  
 資格情報がネットワークのドメイン コントローラーに転送される間に傍受されるリスクを軽減するには、チャネルの暗号化 (Secure Sockets Layer (SSL) など) を使用する必要があります。 基本認証のみを使用した場合、ユーザー名はクリア テキストで転送され、パスワードは Base64 エンコード形式で転送されます。 チャネルの暗号化を追加すると、パケットが読み取り不可能になります。 詳細については、「 [ネイティブ モードのレポート サーバーでの SSL 接続の構成](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md)」を参照してください。  
  
 基本認証を有効にすると、レポートにデータを提供する外部データ ソースへの接続のプロパティをユーザーが設定するときに **[Windows 統合セキュリティ]** オプションを選択できなくなることに注意してください。 このオプションは、データ ソース プロパティ ページでグレー表示されます。  
  
> [!NOTE]  
>  次に示す手順は、ネイティブ モードのレポート サーバーを対象としています。 レポート サーバーを SharePoint 統合モードで配置する場合は、Windows 統合セキュリティを指定する既定の認証設定を使用する必要があります。 レポート サーバーでは、既定の Windows 認証拡張機能の内部機能を使用して、SharePoint 統合モードのレポート サーバーがサポートされます。  
  
### <a name="to-configure-a-report-server-to-use-basic-authentication"></a>レポート サーバーを構成して基本認証を使用するには  
  
1.  テキスト エディターで RSReportServer.config を開きます。  
  
     ファイルはある*\<ドライブ >:*\Program Files\Microsoft SQL Server\MSRS13 です。MSSQLSERVER\Reporting services \reportserver にあります。  
  
2.  検索\<**認証**>。  
  
3.  次に示す XML 構造の中でニーズに最も合うものをコピーします。 最初の XML 構造には、次のセクションで説明するすべての要素を指定するためのプレースホルダーが含まれています。  
  
    ```  
    <Authentication>  
          <AuthenticationTypes>  
                 <RSWindowsBasic>  
                       <LogonMethod>3</LogonMethod>  
                       <Realm></Realm>  
                       <DefaultDomain></DefaultDomain>  
                 </RSWindowsBasic>  
          </AuthenticationTypes>  
          <EnableAuthPersistence>true</EnableAuthPersistence>  
    </Authentication>  
    ```  
  
     既定値を使用する場合は、次に示す最小限の要素構造をコピーしてください。  
  
    ```  
          <AuthenticationTypes>  
                 <RSWindowsBasic/>  
          </AuthenticationTypes>  
    ```  
  
4.  既存のエントリを貼り付けます\<**認証**>。  
  
     複数の種類の認証を使用している場合は、 **RSWindowsBasic** 要素のみを追加し、 **RSWindowsNegotiate**、 **RSWindowsNTLM**、 **RSWindowsKerberos**の各エントリは削除しないようにします。  
  
     **Custom** は他の認証の種類と併用できないので注意してください。  
  
5.  空の値を置き換えます\<**レルム**> または\<**例えば**> 環境内で有効な値を使用します。  
  
6.  ファイルを保存します。  
  
7.  スケールアウト配置を構成した場合は、配置内の他のレポート サーバーに対して上記の手順を繰り返します。  
  
8.  レポート サーバーを再起動して、現在開いているセッションを消去します。  
  
## <a name="rswindowsbasic-reference"></a>RSWindowsBasic リファレンス  
 基本認証を構成するときには次の要素を指定できます。  
  
|要素|必須|有効な値|  
|-------------|--------------|------------------|  
|LogonMethod|可<br /><br /> 値を指定しない場合は 3 が使用されます。|**2** = ネットワーク ログオン。プレーン テキスト パスワードを認証する高パフォーマンス サーバー向けです。<br /><br /> **3** = クリア テキスト ログオン。各 HTTP 要求と一緒に送信される認証パッケージにログオン資格情報が保持されます。これにより、ネットワーク内の他のサーバーに接続する際に、サーバーがユーザーの権限を借用できます (既定値)。<br /><br /> 注: 値 0 (対話型ログオン) と値 1 (バッチ ログオン) は、 **では** サポートされません [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]。|  
|Realm|省略可|組織内の保護されたリソースへのアクセスを制御するための承認機能や認証機能を含んだリソース パーティションを指定します。|  
|DefaultDomain|省略可|サーバーがユーザーを認証する際のドメインを指定します。 この値はオプションです。ただし、省略した場合、レポート サーバーでは、コンピューター名がドメインとして使用されます。 コンピューターがドメインのメンバーになっている場合は、そのドメインが既定のドメインです。 レポート サーバーをドメイン コントローラーにインストールした場合、そのコンピューターによって制御されるドメインを指定します。|  
  
## <a name="see-also"></a>参照  
 [レポート サーバー アプリケーションのアプリケーション ドメイン](../../reporting-services/report-server/application-domains-for-report-server-applications.md)   
 [Reporting Services のセキュリティと保護](../../reporting-services/security/reporting-services-security-and-protection.md)  
  
  

