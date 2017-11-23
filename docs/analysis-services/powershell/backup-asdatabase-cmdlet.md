---
title: "Backup-asdatabase コマンドレット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: powershell
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 03d58a82-021c-4e13-b265-c084f42a8bb2
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: cc648f0ad73c9ed39f49e823fe4293b57ff0d470
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="backup-asdatabase-cmdlet"></a>Backup-ASDatabase コマンドレット

[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Analysis Services の多次元形式または表形式のデータベースを Analysis Services のバックアップ ファイル (.abf) にバックアップします。  

>[!NOTE] 
>この記事には、古くなった情報と例があります。 最新バージョンには、Get-help コマンドレットを使用します。
  
## <a name="syntax"></a>構文  
 `Backup-ASDatabase [-BackupFile] <string> [-Name] <string> [-AllowOverwrite <SwitchParameter>] [-BackupRemotePartitions <SwitchParameter>] [-ApplyCompression <SwitchParameter>] [-FilePassword <SecureString>] [-Locations <Microsoft.AnalysisServices.BackupLocation[]>] [-Server <string>] [-Credential <PSCredential>] [<CommonParameters>]`  
  
 `Backup-ASDatabase –Database <Microsoft.AnalysisServices.Database> [-AllowOverwrite <SwitchParameter>] [-BackupRemotePartitions <SwitchParameter>] [-ApplyCompression <SwitchParameter>] [-FilePassword <SecureString>] [-Locations <Microsoft.AnalysisServices.BackupLocation[]>] [-Server <string>] [-Credential <PSCredential>] [<CommonParameters>]`  
  
## <a name="description"></a>Description  
 Analysis Services システム管理者は、多次元形式または表形式のデータベースをバックアップ ファイルにバックアップすることができます。 場所を指定しない場合は、セットアップ中に指定された既定のバックアップ場所が使用されます。  
  
 バックアップ ファイルを暗号化することができます。 –FilePassword を使用して、ファイルを暗号化します。 後でデータベースを復元するときに、暗号化した際に指定したものと同じパスワードを入力する必要があります。  
  
 このコマンドレットは、HTTP アクセスに対して Analysis Services インスタンスを構成している場合に使用できる、–Credential パラメーターをサポートします。 –Credential パラメーターは、Windows のユーザー ID を提供する PSCredential オブジェクトを受け取ります。 IIS は、Analysis Services に接続する際、このユーザーの権限を借用します。 バックアップを実行するために、この ID には、Analysis Services インスタンスに対するシステム管理者権限が必要です。  
  
## <a name="parameters"></a>パラメーター  
  
### <a name="-backupfile-string"></a>-Backupfile\<文字列 >  
 バックアップ ファイルのパスおよび名前を指定します。 パスを含まないファイル名だけを指定する場合は、既定のバックアップの場所が使用されます。 このパラメーターは、–Name パラメーターと組み合わせる場合のみ使用できます。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|0|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-name-string"></a>-名前\<文字列 >  
 バックアップ対象の Analysis Services データベースを指定します。 名前を文字列として渡す場合は、Database パラメーターまたは –Name パラメーターを使用してデータベースを指定することができます。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|1|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-allowoverwrite-switchparameter"></a>-Allowoverwrite \<SwitchParameter >  
 同じ名前のバックアップ ファイルを上書きします。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-backupremotepartitions-switchparameter"></a>-Backupremotepartitions \<SwitchParameter >  
 リモート パーティションがバックアップに含まれるかどうかを指定します。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-applycompressionswitchparameter"></a>-ApplyCompression\<SwitchParameter >  
 バックアップ ファイルを圧縮するかどうかを指定します。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-filepassword-securestring"></a>-Filepassword \<SecureString >  
 バックアップ ファイルの暗号化に使用するパスワードを指定します。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-locations-microsoftanalysisservicesbackuplocation"></a>-場所\<Microsoft.AnalysisServices.BackupLocation >  
 バックアップ ファイルを格納する場所を指定します。  
  
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
  
### <a name="-database-microsoftanalysisservicesdatabase"></a>-データベース\<Microsoft.AnalysisServices.Database >  
 バックアップ対象の Analysis Services データベース オブジェクトを指定します。 -Database パラメーターまたは –Name パラメーターを使用してデータベースを指定できます。 データベース名をパイプする場合は、–Database を使用します。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|true|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="commonparameters"></a>\<CommonParameters >  
 このコマンドレットは、-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer、および –OutVariable の共通パラメーターをサポートしています。 詳細については、「 [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825)」を参照してください。  
  
## <a name="inputs-and-outputs"></a>入力および出力  
 入力型は、コマンドレットにパイプできるオブジェクトの型です。 戻り値の型は、コマンドレットが返すオブジェクトの型です。  
  
|||  
|-|-|  
|入力|Microsoft.AnalysisServices.Database<br /><br /> 特定のインスタンスのすべてのデータベースなど、バックアップ対象の複数のデータベースをパイプできます。|  
|出力|[なし] :|  
  
## <a name="example-1"></a>例 1  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default >backup-asdatabase awdb-20110930.abf “Adventure Works” -AllowOverwrite -ApplyCompression  
```  
  
 このコマンドは、Adventure Works データベースを既定のバックアップの場所で .abf ファイルにバックアップします。 その場所に同じ名前の既存のファイルが存在する場合、そのファイルは上書きされます。  
  
## <a name="example-2"></a>例 2  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default >$AWDB = get-item “databases\Adventure Works”   
PS SQLSERVER:\SQLAS\Localhost\default >Backup-asdatabase –database:$AWDB –AllowOverwrite  
```  
  
 このコマンドは、-Backupfile および -Name の代わりに –Database を使用します。 データベース名をコマンドレットにパイプする場合は、–Database パラメーターを使用します。  
  
## <a name="example-3"></a>例 3  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default\databases >dir * | backup-asdatabase  
```  
  
 このコマンドは、ローカル サーバーのすべてのデータベースをバックアップします。  
  
## <a name="example-4"></a>例 4  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default > $pwd = read-host –AsSecureString –Prompt “Password”   
PS SQLSERVER:\SQLAS\Localhost\default > $pwd -is [System.IDisposable]   
PS SQLSERVER:\SQLAS\Localhost\default > backup-asdatabase –backupfile test.abf –name contoso_retail –filepassword:$pwd server myremoteserver  
PS SQLSERVER:\SQLAS\Localhost\default >$pwd.Dispose()  
PS SQLSERVER:\SQLAS\Localhost\default >Remove-Variable –Name pwd  
```  
  
 行 1 と 2 を使用して、ファイルの暗号化に使用されるパスワードを要求します。  
  
 行 3 は、リモート Analysis Services サーバーの Contoso_Retail サンプル データベースを、同様にリモート サーバーにある test.abf という名前の Analysis Services バックアップ ファイルにバックアップします。 ファイルは、既定のインスタンスの既定のバックアップ フォルダーに保存されます。  
  
 行 4 と 5 は、パスワードを削除します。  
  
  
  
