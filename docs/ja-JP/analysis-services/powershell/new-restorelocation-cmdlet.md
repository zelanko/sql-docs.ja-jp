---
title: New-restorelocation コマンドレット |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ''
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 43d0ad50544be56628b9aaa48494bb84351eb0ab
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="new-restorelocation-cmdlet"></a>New-RestoreLocation コマンドレット
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  データベースの復元に使用する情報を指定します。  

>[!NOTE] 
>この記事には、古くなった情報と例があります。 最新バージョンには、Get-help コマンドレットを使用します。
  
## <a name="syntax"></a>構文  
 `New-RestoreLocation [-File <String>] [-DataSourceId <String>] [-ConnectionString <String>] [-DataSourceType <RestoreDataSourceType>] [-Folders <RestoreFolder[]>] [-AsTemplate] [-Server <String>] [-Credential <PSCredential>] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]`  
  
 `New-RestoreLocation [-Server <String>] [-Credential <PSCredential>] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]`  
  
 –Verbose、-Debug、-Whatif、–Confirm の各パラメーター、およびエラーと警告のパラメーターなどの一般的なパラメーターは、Windows PowerShell リファレンスに記載されています。 詳細については、「 [about_CommonParameters](http://technet.microsoft.com/library/dd315352.aspx)」を参照してください。  
  
## <a name="description"></a>Description  
 New-RestoreLocation コマンドレットには、データベースの復元に使用される情報が含まれています。サーバーおよびデータベースの接続文字列、データ ソースのプロパティ、復元するデータベースに関連付けられたファイルおよびフォルダーなどです。  
  
## <a name="parameters"></a>パラメーター  
  
### <a name="-file-string"></a>-File \<string>  
 復元するバックアップ ファイルの名前を指定します。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-datasourceid-string"></a>-DataSourceId \<string>  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-connectionstring-string"></a>-ConnectionString \<string>  
 リモート Analysis Services インスタンスの接続文字列を指定します。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-datasourcetype-asrestoredatasourcetype"></a>-DataSourceType \<AS.RestoreDataSourceType>  
 パーティションの場所に基づいて、データ ソースがリモートまたはローカルのどちらであるかを指定します。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-folders-asrestorefolder"></a>-Folders \<AS.RestoreFolder>  
 ローカルまたはリモートのインスタンスのパーティション フォルダーを指定します。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-astemplate-switchparameter"></a>-AsTemplate \<SwitchParameter>  
 オブジェクトをメモリ内に作成して取得するかどうかを指定します。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-server-string"></a>-Server \<string>  
 コマンドレットが接続して実行する Analysis Services インスタンスを指定します。 サーバー名が指定されていない場合は、localhost に接続されます。 既定のインスタンスの場合は、サーバー名のみを指定します。 名前付きインスタンスの場合は、servername \instancename 形式を使用します。 HTTP 接続では、http[s]://server[:port]/virtualdirectory/msmdpump.dll 形式を使用します。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値|localhost|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-credential-pscredential"></a>-Credential \<PSCredential>  
 このパラメーターは、HTTP アクセス用に構成したインスタンスに対して、Analysis Service インスタンスへの HTTP 接続を使用するときに、ユーザー名とパスワードを渡すために使用されます。 詳細については、次を参照してください。[インターネット インフォメーション サービスでの Analysis Services への HTTP アクセスの構成&#40;IIS&#41; 8.0](../../analysis-services/instances/configure-http-access-to-analysis-services-on-iis-8-0.md)の HTTP 接続です。  
  
 このパラメーターを指定した場合は、指定された Analysis Server インスタンスへの接続にユーザー名とパスワードが使用されます。 資格情報を指定していない場合は、ツールを実行しているユーザーの既定の Windows アカウントが使用されます。  
  
 このパラメーターを使用するには、まず、Get-Credential を使用して PSCredential オブジェクトを作成し、ユーザー名とパスワードを指定します ( `$Cred=Get-Credential “adventure-works\bobh”`など)。 その後、このオブジェクトを –Credential パラメーター `(-Credential:$Cred`) にパイプできます。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|True (ByValue)|  
|ワイルドカード文字の受け入れ|オプション|  
  
## <a name="inputs-and-outputs"></a>入力および出力  
 入力型は、コマンドレットにパイプできるオブジェクトの型です。 戻り値の型は、コマンドレットが返すオブジェクトの型です。  
  
|||  
|-|-|  
|入力|なし|  
|出力|なし|  
  
## <a name="examples"></a>使用例  
  
  
