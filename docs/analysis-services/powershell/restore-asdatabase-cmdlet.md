---
title: "Restore-asdatabase コマンドレット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: powershell
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8ab7a2d0-679c-40e6-b9b9-042184b2dfc9
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 96e61c207316b216a1706834188a4f6f235cb52e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="restore-asdatabase-cmdlet"></a>Restore-ASDatabase コマンドレット

[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  多次元形式または表形式のデータベース バックアップ ファイル (.abf) から Analysis Services インスタンスを復元します。  

>[!NOTE] 
>この記事には、古くなった情報と例があります。 最新バージョンには、Get-help コマンドレットを使用します。
  
## <a name="syntax"></a>構文  
 `Restore-ASDatabase [-RestoreFile] <string> [-Name] <string> [-AllowOverwrite <SwitchParameter>] Locations <Microsoft.AnalysisServices.RestoreLocation[]>] [-Security <Microsoft.AnalysisServices.RestoreSecurity>] [-Password <System.SecureString>] [-StorageLocation <System.string>] [-Server <string>] [-Credential <PSCredential>] [<CommonParameters>]`  
  
## <a name="description"></a>Description  
 Analysis Services システム管理者は、多次元形式または表形式のデータベースをバックアップ ファイル (.abf) からローカルまたはリモートのサーバー インスタンスに復元できます。 復元するファイルが暗号化されている場合は、-FilePassword を使用して、ファイルの暗号化を解除するためのパスワードを提供します。  
  
 このコマンドレットは、HTTP アクセスに対して Analysis Services インスタンスを構成している場合に使用できる、–Credential パラメーターをサポートします。 –Credential パラメーターは、Windows のユーザー ID を提供する PSCredential オブジェクトを受け取ります。 IIS は、Analysis Services に接続する際、このユーザーの権限を借用します。 ファイルを復元するために、この ID には、Analysis Services インスタンスに対するシステム管理者権限が必要です。  
  
## <a name="parameters"></a>パラメーター  
  
### <a name="-restorefile-string"></a>-Restorefile &\<文字列 >  
 復元するファイルのパスと名前を指定します。 パスを含まないファイル名だけを指定した場合は、既定のバックアップの場所と見なされます。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|0|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-name-string"></a>-名前\<文字列 >  
 復元対象の Analysis Services データベースを指定します。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|1|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-allowoverwrite-switchparameter"></a>-Allowoverwrite \<SwitchParameter >  
 同じ名前と場所を使用するデータベースが上書きされます。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-locations-microsoftanalysisservicesrestorelocation"></a>-場所\<Microsoft.AnalysisServices.RestoreLocation >  
 復元対象のパーティションのリモートの場所を指定します。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-security-microsoftanalysisservicesrestoresecurity"></a>セキュリティ\<Microsoft.AnalysisServices.RestoreSecurity >  
 復元操作に使用されるセキュリティ設定を表します。 有効な値は、CopyAll、SkipMembership、IgnoreSecurity のいずれかです。 CopyAll はロールおよびメンバーシップを復元します。 SkipMembership はロールのみを再作成します。 IgnoreSecurity はデータベースを復元しますが、ロールは復元しません。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-password-securestring"></a>パスワードの\<SecureString >  
 暗号化されたバックアップ ファイルの復元に使用するパスワードを指定します。 ファイルの暗号化に使用したパスワードを指定する必要があります。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-storagelocation-string"></a>-Storagelocation\<文字列 >  
 データベースのストレージの場所を指定します。 これは、ファイル システム上のデータベース ファイルの場所です。 既定の場所 (ターゲット インスタンスのバックアップ フォルダー) を使用しない場合は、このパラメーターを設定します。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-server-string"></a>-サーバー\<文字列 >  
 コマンドレットが接続して実行する Analysis Services インスタンスを指定します。 サーバー名が指定されていない場合は、localhost に接続されます。 既定のインスタンスの場合は、サーバー名のみを指定します。 名前付きインスタンスの場合は、servername \instancename 形式を使用します。 HTTP 接続では、http[s]://server[:port]/virtualdirectory/msmdpump.dll 形式を使用します。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値|localhost|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-credential-pscredential"></a>-Credential \<PSCredential >  
 Windows ユーザー名とパスワードを提供する PSCredential オブジェクトを指定します。 基本認証を使用して、HTTP アクセスに対する Analysis Services インスタンスを構成している場合のみ、このパラメーターを指定します。 統合セキュリティを使用するネイティブ接続では、このパラメーターは無視されます。  
  
 このパラメーターが存在する場合、パラメーターで提供される資格情報は接続文字列に付加されます。 IIS は、Analysis Services に接続する際、このユーザー ID を借用します。 資格情報を指定していない場合は、ツールを実行しているユーザーの既定の Windows アカウントが使用されます。  
  
 このパラメーターを使用するには、まず、Get-Credential を使用して PSCredential オブジェクトを作成し、ユーザー名とパスワードを指定します ( `$Cred=Get-Credential “adventure-works\admin”`など)。 その後、このオブジェクトを –Credential パラメーター `(-Credential:$Cred`) にパイプできます。  
  
 HTTP アクセスの詳細については、「[インターネット インフォメーション サービス &#40;IIS&#41; 8.0 上の Analysis Services への HTTP アクセスの構成](../../analysis-services/instances/configure-http-access-to-analysis-services-on-iis-8-0.md)」を参照してください。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|True (ByValue)|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="commonparameters"></a>\<CommonParameters >  
 このコマンドレットは、-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer、および –OutVariable の共通パラメーターをサポートしています。 詳細については、「 [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825)」を参照してください。  
  
## <a name="inputs-and-outputs"></a>入力および出力  
 入力型は、コマンドレットにパイプできるオブジェクトの型です。 戻り値の型は、コマンドレットが返すオブジェクトの型です。  
  
|||  
|-|-|  
|入力|System.string<br /><br /> 文字列値をコマンドレットにパイプすることができます。|  
|出力|[なし] :|  
  
## <a name="example-1"></a>例 1  
  
```  
PS SQLSERVER:\SQLAS\localhost\default> restore-asdatabase awtest.abf testawrestoredb –security:CopyAll  
```  
  
 このコマンドは、ローカルのバックアップ フォルダー内にある Analysis Services バックアップ ファイル (awtest.abf) をローカルの Analysis Services の既定のインスタンスに復元します。 データベース名は存在していなくてもかまいません。この場合は、復元操作の一部としてデータベース名を指定します。 -Security:CopyAll を追加すると、バックアップ データベースのロールおよびロールのメンバーシップが、新しく復元されたデータベースに設定されます。  
  
## <a name="example-2"></a>例 2  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default > $pwd = read-host –AsSecureString –Prompt “Password”   
PS SQLSERVER:\SQLAS\Localhost\default > $pwd -is [System.IDisposable]   
PS SQLSERVER:\SQLAS\localhost\default> restore-asdatabase –restorefile testdb.abf –name AWTEST2 –password:$pwd  
PS SQLSERVER:\SQLAS\Localhost\default >$pwd.Dispose()  
PS SQLSERVER:\SQLAS\Localhost\default >Remove-Variable –Name pwd  
```  
  
 行 1 と 2 を使用して、ファイルの暗号化に使用されたパスワードを要求します。  
  
 行 3 は、Analysis Services の既定のインスタンスのローカル バックアップ フォルダーから暗号化された Analysis Services バックアップ ファイル (testdb.abf) を復元します。  
  
 行 4 と 5 は、パスワードを削除します。  
  
## <a name="example-3-remote-scenario"></a>例 3 (リモートのシナリオ)  
 この例では、ファイル共有のローカル バックアップ ファイルを Analysis Services のリモート インスタンスに復元する方法を示します。 この例では、バックアップ ファイルは、 **ssas-aw-srv01** という名前のコンピューター上で、Analysis Services の既定のインスタンスに **internetsales**という名前のデータベースとして復元されます。  
  
 バックアップ ファイルはネットワーク共有に置かれ、パブリック読み取りアクセスが許可されています。 リモートの Analysis Services インスタンスにはファイルの読み取りアクセス許可が必要です。 ファイルの場所は、ネットワーク共有 (ドライブ以外) にする必要があります。  
  
 この例では、SQLAS プロバイダーには依存していません。 コマンドレットはスタンドアロン コマンドとして実行できます。  
  
```  
PS SQLSERVER:\> restore-asdatabase -restorefile "\\FileServer01\DBFiles\InternetSalesTabular.abf" -name "internetsales  
" -server "SSAS-AW-SRV01"  
```  
  
## <a name="example-4"></a>例 4  
  
```  
PS SQLSERVER:\SQLAS\localhost\default> restore-asdatabase –restorefile “\\myremoteserver\backups\testdb.abf” –name Contoso_Retail –server myremoteserver –storagelocation “\\myremoteserver\restoreDBFiles”  
```  
  
 このコマンドは、リモートのバックアップ フォルダー内にある暗号化された Analysis Services バックアップ ファイル (testdb.abf) をリモートの Analysis Services の既定のインスタンスに復元します。 -StorageLocation パラメーターを使用して、データベース ファイルを既定以外の場所 (この場合は restoreDBfiles という名前のファイル共有) に配置します。  
  

