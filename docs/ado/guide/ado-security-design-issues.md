---
title: ADO セキュリティのデザインに関する問題 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ADO, security
ms.assetid: 86b83a38-efdf-4831-a6d5-7e470d517d1c
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f6b8cf26515276ce4dd9338d64746a2b7a017d99
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ado-security-design-features"></a>ADO セキュリティ デザイン機能
以下のセクションで ActiveX データ オブジェクト (ADO) 2.8 およびそれ以降のセキュリティ関連のデザイン機能について説明します。 これらの変更に対する ado 2.8 セキュリティを強化します。 ADO 6.0 では、Windows Vista の Windows DAC 6.0 に含めると、これは、します機能的には、Windows XP および Windows Server 2003 で MDAC 2.8 に含まれていた ADO 2.8。 このトピックでは、最適な ADO 2.8 またはそれ以降では、アプリケーションを保護する方法に関する情報を提供します。

> [!IMPORTANT]
>  ADO の以前のバージョンからアプリケーションを更新する場合は、顧客に展開する前に、非運用環境のコンピューター上で更新されたアプリケーションをテストすることをお勧めします。 これにより、把握するには、互換性の問題の更新されたアプリケーションを展開する前にことを確認できます。

## <a name="internet-explorer-file-access-scenarios"></a>インターネット エクスプ ローラーのファイル アクセスのシナリオ
 影響は次の機能で使用されているときの ADO 2.8 およびそれ以降の機能には、Internet Explorer で Web ページがスクリプト化します。

### <a name="revised-and-improved-security-warning-message-box-now-used-to-alert-users"></a>変更と強化されたセキュリティの警告メッセージ ボックスがユーザーに警告を使用するようになりました
 ADO 2.7 およびそれ以前のスクリプト化された Web ページが信頼されていないプロバイダーから ADO コードを実行しようとするときに、次の警告メッセージが表示されます。

```
This page accesses data on another domain. Do you want to allow this? To
avoid this message in Internet Explorer, you can add a secure Web site to
your Trusted Sites zone on the Security tab of the Internet Options dialog
box.
```

 ADO 2.8 およびそれ以降の前のメッセージは表示されなくなります。 代わりに、このコンテキストで、次のメッセージが表示されます。

```
This Website uses a data provider that may be unsafe. If you trust the
Website, click OK, otherwise click Cancel.
```

 上記のメッセージは、いずれの場合も、影響を把握しながら、十分な情報に基づいて決定を行うユーザーを使用できます。

-   ユーザーは、サイトを信頼する場合は、[ok] をクリックしてできるようになります (すべての ADO メソッドとプロパティが、このトピックの後半で説明されているディスクにアクセス可能な Api の例外) のすべてのディスク セーフ コードを実行し、ブラウザー ウィンドウで実行します。

-   ユーザーが、サイトを信頼していない場合は、ADO のコード全体の実行からのデータ アクセスをブロック キャンセル をクリックします。

### <a name="disk-accessible-code-limited-now-to-trusted-sites"></a>ディスクにアクセス可能なコードが信頼済みサイトに限定ようになりました
 Ado 2.8 具体的には、限られた一連の Api は、読み取りまたはローカル コンピューター上のファイルに書き込みをする可能性が公開される可能性が機能を制限するその他の設計の変更を加えました。 さらにされている API のメソッドをここでは Internet Explorer を実行するときに、安全性の制限します。

-   ADO の**ストリーム**オブジェクトの場合、 [LoadFromFile](../../ado/reference/ado-api/loadfromfile-method-ado.md)または[SaveToFile](../../ado/reference/ado-api/savetofile-method.md)メソッドを使用します。

-   ADO の**レコード セット**オブジェクトをどちらの場合、[保存](../../ado/reference/ado-api/save-method.md)メソッドまたは[開いている](../../ado/reference/ado-api/open-method-ado-recordset.md)場合などのメソッドか、 **adCmdFile**オプションが設定されているまたは[Microsoft OLE DB Persistence Provider (MSPersist)](../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)を使用します。

 これらの制限の可能性のあるディスクにアクセス可能な関数のセット、次の動作は ADO 2.8 以降、Internet Explorer でこれらのメソッドを使用するコードが実行される場合に発生します。

-   コードを提供するサイトは、信頼済みサイト ゾーンの一覧に以前に追加された、コードは、ブラウザーで実行し、ローカル ファイルにアクセスを許可します。

-   サイトが信頼済みサイト ゾーンの一覧に表示されない場合は、コードはブロックされ、ローカル ファイルへのアクセスが拒否されました。

    > [!NOTE]
    >  ADO では 2.8 およびそれ以降、ユーザーがいないまたはメッセージが表示サイトを信頼済みサイト ゾーンの一覧に追加することをお勧めします。 したがって、信頼済みサイトの一覧の管理は、展開またはローカル ファイル システムへのアクセスを必要とする Web サイト ベースのアプリケーションをサポートする者の責任において、します。

### <a name="access-blocked-to-the-activecommand-property-on-recordset-objects"></a>アクセスがレコード セット オブジェクトで ActiveCommand プロパティにブロックされます。
 Internet Explorer での実行中、ADO 2.8 ブロックへのアクセス、 [ActiveCommand](../../ado/reference/ado-api/activecommand-property-ado.md)アクティブなプロパティ**Recordset**オブジェクトし、エラーが返されます。 信頼済みサイト一覧に登録されている Web サイトからのページのものかどうかに関係なく、エラーが発生します。

### <a name="changes-in-handling-for-ole-db-providers-and-integrated-security"></a>OLE DB プロバイダーと統合セキュリティの処理の変更
 ADO 2.7 および潜在的なセキュリティの問題と問題の以前のバージョンを確認中に次のシナリオが検出されます。

 場合によっては、統合セキュリティをサポートしている OLE DB プロバイダーで[DBPROP_AUTH_INTEGRATED](https://msdn.microsoft.com/library/windows/desktop/ms712973.aspx)プロパティは、意図せず他のサーバーに接続する ADO 接続オブジェクトを再利用をスクリプト化された Web ページを許可できます可能性がありますユーザーの現在のログイン資格情報を使用します。 これを回避するのには、ADO 2.8 およびそれ以降は、選択した方法に応じて提供、または、統合セキュリティを提供できませんの OLE DB プロバイダーを処理します。

 サイトが信頼済みサイト ゾーンの一覧に表示されるから読み込まれた Web ページは、次の表は、ADO 2.8 およびそれ以降が各ケースで ADO 接続を管理する方法の詳細を提供します。

|IE の設定、ユーザー認証をログオンします。|"Integrated Security"と UID および PWD、プロバイダーのサポート (SQLOLEDB) を指定します。|プロバイダーは"Integrated Security"(JOLT、MSDASQL、MSPersist) をサポートしていません|プロバイダーは、"Integrated Security"をサポートし、SSPI (UID/PWD が指定されていない) に設定されています。|
|------------------------------------------------|----------------------------------------------------------------------------------------|----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
|現在のユーザー名とパスワードを使用した自動ログオン|接続の許可|接続の許可|接続の許可|
|ユーザー名とパスワードの入力を求める|接続の許可|接続が失敗します。|接続が失敗します。|
|イントラネット ゾーンでのみ自動ログオン|接続の許可|プロンプトを表示するセキュリティの警告|プロンプトを表示するセキュリティの警告|
|匿名ログオン|接続の許可|接続が失敗します。|接続が失敗します。|

 セキュリティ警告ようになりましたが表示される場所の場合、メッセージ ボックスがユーザーに通知します。

```
This Website is using your identity to access a data source. If you trust this Website, click OK, otherwise click Cancel.
```

 上記のメッセージは、ユーザーがより的確な意思決定を行うし、続行できます。

> [!NOTE]
>  信頼されていないサイト (つまり、サイトで信頼済みサイト ゾーンの一覧に表示されない)、プロバイダーも (このセクションで説明したように) として信頼されていない場合は、ユーザーを参照してください行と、安全でないプロバイダーに関する警告と 2 番目の警告の 2 つのセキュリティ警告、自身の id を使用しようとしてください。 ユーザーは、最初の警告 に ok をクリックすると、Internet Explorer の設定および応答動作コードが上の表で説明されているが実行されます。

## <a name="controlling-whether-password-text-is-returned-in-ado-connection-strings"></a>ADO 接続文字列にパスワードのテキストを返すかどうかを制御します。
 値を取得するとき、 [ConnectionString](../../ado/reference/ado-api/connectionstring-property-ado.md)プロパティを ADO**接続**オブジェクトを次のイベントが発生します。

1.  接続が開いている場合は、初期化の呼び出しし、に対する基になる OLE DB プロバイダー接続文字列を取得します。

2.  OLE DB プロバイダーの設定に応じて、 [DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO](https://msdn.microsoft.com/library/windows/desktop/ms714905.aspx)プロパティ、パスワードは返されるその他の接続文字列情報と共に含まれています。

 たとえば場合、ADO 接続の動的プロパティ**Persist Security Info**に設定されている**True**、パスワード情報が返される接続文字列に含まれています。 それ以外の場合、基になるプロバイダーが設定されている場合、プロパティ**False** (たとえば、SQLOLEDB プロバイダーと共に)、パスワードの情報を省略すると、返される接続文字列にします。

 サード パーティ製を使用している場合 (つまり、Microsoft 以外) ADO アプリケーション コードで、OLE DB プロバイダーがチェックされる方法、 **DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO**を決定するプロパティを実装するかどうかを含めることADO 接続文字列にパスワード情報が許可されます。

## <a name="checking-for-non-file-devices-when-loading-and-saving-recordsets-or-streams"></a>非ファイル デバイスの読み込み、レコード セットまたはストリームを保存するときの確認
 ADO 2.7 およびそれ以前のファイル入力/出力操作など[開く](../../ado/reference/ado-api/open-method-ado-recordset.md)と[保存](../../ado/reference/ado-api/save-method.md)で読み書き可能なファイル ベースのデータによってにより、URL またはファイル名を使用するディスク以外を指定に使用されました。ファイルの種類に基づいています。 たとえば、LPT1、COM2、PRN です。TXT、AUX のプリンターと補助デバイス間でシステムを使用して、特定の入力/出力の別名として使用できません。

 ADO 2.8 およびそれ以降、この機能が更新されました。 オープンと保存の**Recordset**と**ストリーム**オブジェクト、ADO は今すぐ URL またはファイル名で指定された入力または出力のデバイスが実際のファイルであることを確認するファイルの種類チェックを実行します。

> [!NOTE]
>  ファイルの型チェックこのセクションで説明したようにのみ適用されます Windows 2000 以降。 Windows 98 などの以前の Windows リリース ADO 2.8 またはそれ以降が実行されている場合に適用されません。
