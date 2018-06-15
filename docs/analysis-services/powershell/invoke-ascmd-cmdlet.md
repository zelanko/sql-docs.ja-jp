---
title: Invoke-ascmd コマンドレット |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: powershell
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cf570da0e7be70fda804a3f17d11f6c8498c1605
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34027812"
---
# <a name="invoke-ascmd-cmdlet"></a>Invoke-ASCmd コマンドレット
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  データベース管理者は、XMLA スクリプト、多次元式 (MDX)、データ マイニング拡張機能 (DMX) ステートメント、または表形式モデル スクリプト言語 (TMSL) スクリプトを実行できます。  
  
 TMSL は、SQL Server 2016 Analysis Services インスタンス上の表形式サーバー モードでのみサポートされます。  
  
 データベースまたはその他のオブジェクトを作成する場合は、これのコマンドレットをスクリプト入力ファイルと共に使用します。  
  
## <a name="syntax"></a>構文  
 `Invoke-ASCmd –Query <string> [-Server <string>] [-Database <string>] [-Credential <PSCredential>] [-ConnectionTimeout <int>] [-QueryTimeout <int>] [-Variable <string[]>] [-TraceFile <string>] [-TraceFileFormat <TraceFileFormatOption>] [-TraceFileDelimiter <string>] [-TraceTimeout <int>] [-TraceLevel <TraceLevelOption>] [<CommonParameters>]`  
  
 `Invoke-ASCmd –InputFile <string> [-Server <string>] [-Database <string>] [-Credential <PSCredential>] [-ConnectionTimeout <int>] [-QueryTimeout <int>] [-Variable <string[]>] [-TraceFile <string>] [-TraceFileFormat <TraceFileFormatOption>] [-TraceFileDelimiter <string>] [-TraceTimeout <int>] [-TraceLevel <TraceLevelOption>] [<CommonParameters>]`  
  
## <a name="description"></a>Description  
 Invoke ASCmd コマンドレットは、入力ファイルに含まれるクエリまたはスクリプトを実行できます。  
  
 XMLA でサポートされるコマンド: Alter、Backup、Batch、BeginTransaction、Cancel、ClearCache、CommitTransaction、Create、Delete、DesignAggregations、Drop、Insert、Lock、MergePartitions、NotifyTableChange、Process、Restore、RollbackTransaction、Statement (MDX クエリと DMX ステートメントの実行に使用)、Subscribe、Synchronize、Unlock、Update、UpdateCells。  
  
 TMSL でサポートされるコマンド: Alter、Create、Delete、MergePartitions、Process、Update。  
  
 このコマンドレットは、HTTP アクセスに対して Analysis Services インスタンスを構成している場合に使用できる、–Credential パラメーターをサポートします。 –Credential パラメーターは、Windows のユーザー ID を提供する PSCredential オブジェクトを受け取ります。 IIS は、Analysis Services に接続する際、このユーザーの権限を借用します。 スクリプトを実行するために、この ID には、Analysis Services インスタンスに対するシステム管理者権限が必要です。  
  
## <a name="parameters"></a>パラメーター  
  
### <a name="-query-string"></a>-クエリ\<文字列 >  
 ファイル内にではなくコマンド ラインから直接、実際のスクリプト、クエリ、またはステートメントを指定します。 パイプライン入力としてクエリを指定することもできます。 **Invoke-AsCmd** を使用するときは、 **–InputFile** または **–Query**パラメーターの値を指定する必要があります。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|True (ByValue)|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-inputfile-string"></a>-Inputfile/-i\<文字列 >  
 XMLA スクリプト、MDX クエリ、DMX ステートメント、または TMSL スクリプト (JSON 形式) が記述されているファイルを指定します。 **Invoke-AsCmd** を使用するときは、 **–InputFile** または **–Query**パラメーターの値を指定する必要があります。  
  
|||  
|-|-|  
|必須/省略可能|true|  
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
  
### <a name="-database-string"></a>-Database \<string>  
 MDX クエリまたは DMX ステートメントの実行対象であるデータベースを指定します。 XMLA スクリプトにはデータベース名が埋め込まれているため、コマンドレットで XMLA スクリプトを実行する場合、Database パラメーターは無視されます。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-credential-pscredential"></a>-Credential \<PSCredential>  
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
  
### <a name="-connectiontimeout-int"></a>-Connectiontimeout & \<int >  
 Analysis Services インスタンスへの接続がタイムアウトするまでの秒数を指定します。タイムアウト値には、0 ～ 65,534 の範囲の整数値を指定する必要があります。 0 を指定した場合、接続の試行はタイムアウトしません。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値|30|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-querytimeout-int"></a>-Querytimeout \<int >  
 クエリがタイムアウトになる時間を秒単位で指定します。タイムアウト値を指定しない場合、クエリはタイムアウトしません。タイムアウトには、1 ～ 65,535 の範囲の整数値を指定してください。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値|30|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-variable-string"></a>-可変\<string[] >  
 追加のスクリプト変数を指定します。 各変数は、名前と値のペアです。 スペースや制御文字が値に含まれている場合は、二重引用符で囲む必要があります。 複数の変数とその値を指定するには、PowerShell 配列を使用します。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-tracefile-string"></a>-Tracefile &\<文字列 >  
 XMLA スクリプト、MDX クエリ、または DMX ステートメントを実行しているときに Analysis Services トレース イベントを受け取るファイルを指定します。 ファイルが既に存在する場合は、自動的にそのファイルが上書きされます (-TraceLevel:Duration および –TraceLevel:DurationResult パラメーター設定を使用して作成されるトレース ファイルは例外です)。 空白文字を含むファイル名は引用符 (" ") で囲む必要があります。 ファイル名が無効な場合は、エラー メッセージが生成されます。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-tracefileformat-string"></a>-Tracefileformat &\<文字列 >  
 –TraceFile パラメーター (このパラメーターを指定している場合) のファイル形式を指定します。 使用できるオプションは text または csv です。 既定値は "csv" です。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値|csv|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-tracefiledelimiter-string"></a>-Tracefiledelimiter &\<文字列 >  
 トレース ファイルの形式として csv を指定している場合は、どの文字をトレース ファイルの区切り記号として使用するかを指定します。 既定値は | (パイプ、つまり縦棒) です。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-tracetimeout-int"></a>-Tracetimeout & \<int >  
 トレースを終了するまで Analysis Services エンジンが待機する秒数を指定します (–TraceFile パラメーターを指定している場合)。 指定された秒数の間、トレース メッセージが記録されなかった場合、トレースが終了したと見なされます。 トレース タイムアウトの既定値は 5 秒です。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値|5|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-tracelevel-traceleveloption"></a>-Tracelevel \<TraceLevelOption >  
 トレース ファイルにどのようなデータを集めて記録するかを指定します。 指定できる値は、High、Medium、Low、Duration、DurationResult です。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値|高|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="commonparameters"></a>\<CommonParameters>  
 このコマンドレットは、-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer、および –OutVariable の共通パラメーターをサポートしています。 詳細については、「 [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825)」を参照してください。  
  
## <a name="inputs-and-outputs"></a>入力および出力  
 入力型は、コマンドレットにパイプできるオブジェクトの型です。 戻り値の型は、コマンドレットが返すオブジェクトの型です。  
  
|||  
|-|-|  
|入力|PSObject|  
|出力|文字列|  
  
## <a name="example-1-xmla-input-file"></a>例 1 (XMLA 入力ファイル)  
  
```  
Invoke-ASCmd –InputFile:"C:\MyFolder\DiscoverConnections.xmla"  
```  
  
 このコマンドは、サーバー上のアクティブな接続の一覧を返す XMLA スクリプトを実行します。 DiscoverConnections.xmla ファイルには次の XMLA スクリプトが含まれています。  
  
```  
<Discover xmlns="urn:schemas-microsoft-com:xml-analysis">  
<RequestType>DISCOVER_CONNECTIONS</RequestType>  
<Restrictions />  
   <Properties>  
      <PropertyList>  
         <Content>Data</Content>  
      </PropertyList>  
   </Properties>  
</Discover>  
```  
  
## <a name="example-2-tmsl-input-file"></a>例 2 (TMSL 入力ファイル)  
 この例は、スクリプトが TMSL (JSON) であり、SQL Server 2016 の表形式インスタンスを必要とする点を除いて、最初の例と同じです。 TMSL スクリプトは、SQL Server Management Studio で生成できます。  
  
 複数のインスタンスがあり、表形式インスタンスが名前付きインスタンスである場合は、必ずサーバー名を設定してください。  
  
```  
Invoke-ASCmd –InputFile "C:\folder-name\T1200-NewDB.json" -Server "server-name\instance-name"  
```  
  
## <a name="example-3-query"></a>例 3 (クエリ)  
  
```  
Invoke-ASCmd -Database:"Adventure Works DW" -Query:"<Discover xmlns='urn:schemas-microsoft-com:xml analysis'><RequestType>DISCOVER_DATASOURCES</RequestType><Restrictions></Restrictions><Properties></Properties></Discover>"  
```  
  
 XMLA 検出クエリは、分析サーバーで使用できるデータ ソースとそれらに接続するために必要な情報を返します。 結果は XML 内です。 読みやすくするために、出力を XML ファイルにパイプして (たとえば、 `| Out-file C:\Results\XMLAQueryOutput.xml` をコマンドに追加する)、ブラウザーまたは構造化された XML をサポートする他のアプリケーションに結果を表示することができます。  
  
  
  
