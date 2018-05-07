---
title: プログラムによるパスワードの変更 |Microsoft ドキュメント
description: SQL Server の OLE DB Driver を使用してプログラムからパスワードの変更
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], password expiration
- OLE DB Driver for SQL Server, passwords
- passwords [SQL Server], expiration
- MSOLEDBSQL, password expiration
- expiration [OLE DB Driver for SQL Server]
- passwords [SQL Server], modifying
- expired passwords [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, password expiration
- modifying passwords
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 8ac5c5c127b67fb872a6b10ffc7bd32ec7458092
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="changing-passwords-programmatically"></a>プログラムによるパスワードの変更
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] より前のリリースでは、ユーザーのパスワードの有効期限が切れたとき、そのパスワードをリセットできるのは管理者だけでした。 以降で[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]、OLE DB Driver for SQL Server のサポートへの変更と OLE DB ドライバーを通じてプログラムによってパスワードの有効期限を処理、 **SQL Server ログイン** ダイアログ ボックス。  
  
> [!NOTE]  
>  可能であれば、実行時にユーザーの資格情報を入力し、それらの資格情報を永続的な形式で保存しないように求めるメッセージが表示されます。 自分の資格情報を永続化する必要がある場合、それらを暗号化する必要がありますを使用して、 [Win32 crypto API](http://go.microsoft.com/fwlink/?LinkId=64532)です。 パスワードの使用に関する詳細については、次を参照してください。[強力なパスワードの](../../../relational-databases/security/strong-passwords.md)します。  
  
## <a name="sql-server-login-error-codes"></a>SQL Server ログイン エラー コード  
 認証の問題により接続できない場合、アプリケーションでは次のいずれかの SQL Server エラー コードを使用して、診断と復旧に役立てることができます。  
  
|SQL Server エラー コード|エラー メッセージ|  
|---------------------------|-------------------|  
|15113|ユーザー '%.*ls' はログインできませんでした。理由: パスワードの検証に失敗しました。 アカウントはロックアウトされています。|  
|18463|ユーザー '%.*ls' はログインできませんでした。 理由: パスワードを変更できませんでした。 この時点ではパスワードを使用できません。|  
|18464|ユーザー '%.*ls' はログインできませんでした。 理由: パスワードを変更できませんでした。 このパスワードは短すぎるので、Windows ポリシーの要件を満たしません。|  
|18465|ユーザー '%.*ls' はログインできませんでした。 理由: パスワードを変更できませんでした。 パスワードは長すぎるために、ポリシーの要件を満たしていません。|  
|18466|ユーザー '%.*ls' はログインできませんでした。 理由: パスワードを変更できませんでした。 このパスワードはあまり複雑ではないので、Windows のポリシー要件を満たしません。|  
|18467|ユーザー '%.*ls' はログインできませんでした。 理由: パスワードを変更できませんでした。 パスワードがパスワード フィルター DLL の要件を満たしていません。|  
|18468|ユーザー '%.*ls' はログインできませんでした。 理由: パスワードを変更できませんでした。 パスワードの検証で予期しないエラーが発生しました。|  
|18487|ユーザー '%.*ls' はログインできませんでした。 理由: このアカウントのパスワードの有効期限が切れています。|  
|18488|ユーザー '%.*ls' はログインできませんでした。 理由: このアカウントのパスワードを変更する必要があります。|  
  
## <a name="ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server  
 ユーザー インターフェイスに、OLE DB Driver for SQL Server がパスワードの有効期限をサポートし、プログラムでします。  
  
### <a name="ole-db-user-interface-password-expiration"></a>OLE DB ユーザー インターフェイスによるパスワード期限切れの処理  
 SQL Server の OLE DB Driver に行われた変更によってパスワードの有効期限をサポートしている、 **SQL Server ログイン** ダイアログ ボックス。 DBPROP_INIT_PROMPT の値を DBPROMPT_NOPROMPT に設定すると、パスワードの有効期限が切れている場合に、最初の接続試行が失敗します。  
  
 DBPROP_INIT_PROMPT は、その他の値に設定されています場合、ユーザーは、 **SQL Server ログイン**ダイアログ ボックスで、パスワードが期限切れかどうかに関係なく、します。 ユーザーをクリックすると、**オプション**ボタンをクリックし、確認**パスワードの変更**パスワードを変更します。  
  
 ユーザーが [ok] をクリックするし、パスワードが期限切れ、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]と新しいパスワードを使用して、確認入力を求める、 **SQL Server のパスワードの変更**ダイアログ。  
  
#### <a name="ole-db-prompt-behavior-and-locked-accounts"></a>OLE DB プロンプトの動作とロックされたアカウント  
 アカウントがロックされていることにより、接続に失敗することがあります。 この場合、表示された後、 **SQL Server ログイン**ダイアログ ボックスで、サーバーのエラー メッセージがユーザーに表示および接続の試行が中止されました。 次の表示のことがあります、 **SQL Server のパスワードの変更**ダイアログの場合は、古いパスワードの無効な値を入力します。 この場合も同じエラー メッセージが表示され、接続試行が中止されます。  
  
#### <a name="ole-db-connection-pooling-password-expiration-and-locked-accounts"></a>OLE DB 接続プーリング、パスワードの期限切れ、およびロックされたアカウント  
 接続プール内で接続がアクティブな状態になっている間に、アカウントがロックされたり、そのアカウントのパスワードの有効期限が切れたりすることがあります。 サーバーでは、期限切れのパスワードとロックされたアカウントを 2 回チェックします。 最初のチェックは、初回接続時に行われます。 2 回目のチェックは、接続のリセット時、接続がプールから取り除かれるときに行われます。  
  
 リセットの試行が失敗すると、その接続はプールから削除され、エラーが返されます。  
  
### <a name="ole-db-programmatic-password-expiration"></a>OLE DB プログラムによるパスワード期限切れの処理  
 SQL Server の OLE DB Driver は、DBPROPSET_SQLSERVERDBINIT プロパティ セットに追加された SSPROP_AUTH_OLD_PASSWORD (型 VT_BSTR) プロパティの追加によってパスワードの有効期限をサポートします。  
  
 既存の "Password" プロパティは DBPROP_AUTH_PASSWORD を参照し、新しいパスワードを保存する場合に使用されます。  
  
> [!NOTE]  
>  接続文字列の "Old Password" プロパティは SSPROP_AUTH_OLD_PASSWORD に設定され、現在の (または期限切れの) パスワードが設定されます。このパスワードをプロバイダー文字列のプロパティ経由で使用することはできません。  
  
 プロバイダーでは、このプロパティの値が保存されません。 このプロパティを設定すると新しい接続が行われるので、プロバイダーでは最初の接続に接続プールが使用されません。 パスワード変更が正常に行われた場合でも、現在の接続にはまだ古いパスワードが含まれているので再利用できません。古いパスワードとは、変更後に無効になるパスワードのことです。 また、ログインに成功すると、このプロパティはクリアされます。 クリア後に古いパスワードを取得しようとすると、VT_EMPTY が返されます。  
  
> [!NOTE]  
>  SSPROP_AUTH_OLD_PASSWORD は、パスワードの有効期限が切れたときにしか使用されないので、保存しないでください。  
  
 "Old Password" プロパティが設定されると、プロバイダーでは、パスワードの変更が試行されていることが想定されます。ただし、Windows 認証も指定されている場合は除きます。この場合は、常に Windows 認証が優先されるためです。  
  
 かどうか、古いパスワードが指定されて必須またはオプションとして、それぞれと dbpropstatus _ の状態の値に応じて、DB_E_ERRORSOCCURRED または DB_S_ERRORSOCCURRED のいずれかでの結果を古いパスワードを指定するか Windows 認証を使用する場合返される CONFLICTINGBADVALUE *dwStatus*です。 これが検出されたときに**idbinitialize::initialize**と呼びます。  
  
 パスワード変更の試行が予期せず失敗すると、サーバーからエラー コード 18468 が返されます。 接続試行からは標準の OLE DB エラーが返されます。  
  
 DBPROPSET_SQLSERVERDBINIT プロパティ セットに関する詳細については、次を参照してください。[初期化プロパティと承認プロパティ](../../oledb/ole-db-data-source-objects/initialization-and-authorization-properties.md)です。  

  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server の機能](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
