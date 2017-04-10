---
title: "Merge-Partition コマンドレット | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 15c7b069-897d-4bc8-a808-59cbeeabe4d8
caps.latest.revision: 9
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 9
---
# Merge-Partition コマンドレット
  1 つ以上のマージ元パーティションのデータをマージ先パーティションにマージします。その後、マージ元パーティションを削除します。  
  
## 構文  
 `Merge-ASDatabase [-Name] <string> [-SourcePartitions] <System.String[]> -Database <string> -Cube <string> -MeasureGroup <string> [-Server <string>] [-Credentials <PSCredential>] [<CommonParameters>]`  
  
 `Merge-ASDatabase -TargetPartition <Microsoft.AnalysisServices.Partition> [-SourcePartitions] <System.String[]> -Database <string> -Cube <string> -MeasureGroup <string> [-Server <string>] [-Credentials <PSCredential>] [<CommonParameters>]`  
  
## Description  
 Merge-Partition コマンドレットでは、1 つ以上のマージ元パーティションのデータをマージ先パーティションにマージします。その後、マージ元パーティションを削除します。 パーティションは、次の基準をすべて満たす場合のみマージできます。  
  
-   各パーティションが同じメジャー グループに属している。  
  
-   パーティションが同じコンピューター上にある。  
  
-   パーティションが同じストレージ モード (多次元データベース用の MOLAP、HOLAP、および ROLAP) を共有する。  
  
## パラメーター  
  
### -Name \<string>  
 マージ元パーティション データをマージするマージ先パーティションを指定します。 このパーティションは既に存在している必要があります。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|0|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### -SourcePartition \<string>  
 マージ先パーティションにマージするマージ元パーティションを指定します。 マージするパーティションのコンマ区切りのリストを作成できます。 リストを保存するために変数を使用します。 たとえば、$Sources="Sales_2008", "Sales_2009", "Sales_2010" のように指定できます。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|1|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### -Database \<string>  
 パーティションが属するデータベースを指定します。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### -Cube \<string>  
 パーティションが属するキューブを指定します。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### -MeasureGroup \<string>  
 パーティションが属するメジャー グループを指定します。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### -Server \<string>  
 コマンドレットが接続して実行する Analysis Services インスタンスを指定します。 サーバー名が指定されていない場合は、localhost に接続されます。 既定のインスタンスの場合は、サーバー名のみを指定します。 名前付きインスタンスの場合は、servername \instancename 形式を使用します。 HTTP 接続では、http[s]://server[:port]/virtualdirectory/msmdpump.dll 形式を使用します。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値|localhost|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### -Credential \<PSCredential>  
 このパラメーターは、HTTP アクセス用に構成したインスタンスに対して、Analysis Service インスタンスへの HTTP 接続を使用するときに、ユーザー名とパスワードを渡すために使用されます。 詳細については、「[インターネット インフォメーション サービス (IIS) 8.0 上の Analysis Services への HTTP アクセスの構成](../../analysis-services/instances/configure http access to analysis services on iis 8.0.md)」と「[Analysis Services での PowerShell スクリプティング](../../analysis-services/instances/powershell-scripting-in-analysis-services.md)」の HTTP 接続に関する記述を参照してください。  
  
 このパラメーターを指定した場合は、指定された Analysis Server インスタンスへの接続にユーザー名とパスワードが使用されます。 資格情報を指定していない場合は、ツールを実行しているユーザーの既定の Windows アカウントが使用されます。  
  
 このパラメーターを使用するには、まず、Get-Credential を使用して PSCredential オブジェクトを作成し、ユーザー名とパスワードを指定します (`$Cred=Get-Credential “adventure-works\bobh”` など)。 その後、このオブジェクトを –Credential パラメーター `(-Credential:$Cred`) にパイプできます。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|True (ByValue)|  
|ワイルドカード文字の受け入れ|オプション|  
  
### -TargetPartition \<Microsoft.AnalysisServices.Partition>  
 マージ元パーティションをマージするマージ先パーティションを指定します。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|true|  
|ワイルドカード文字の受け入れ|オプション|  
  
### \<CommonParameters>  
 このコマンドレットは、-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer、および –OutVariable の共通パラメーターをサポートしています。 詳細については、「[About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825)」を参照してください。  
  
## 入力および出力  
 入力型は、コマンドレットにパイプできるオブジェクトの型です。 戻り値の型は、コマンドレットが返すオブジェクトの型です。  
  
|||  
|-|-|  
|入力|System.string|  
|出力|なし|  
  
## 例 1  
 `PS SQL SERVER:\sqlas\locahost\default\Databases\AWTEST\Cubes\Adventure Works\MeasureGroups\sales orders\partitions> $Source=”Total_Orders_2001”, “Total_Orders_2002”, “Total_Orders_2003”` `PS SQL SERVER:\sqlas\locahost\default\Databases\AWTEST\Cubes\Adventure Works\MeasureGroups\sales orders\partitions> Merge-Partition –Name “Total_Orders_2004” –SourcePartitions:$Source –database “AWTEST” –cube “Adventure Works” –MeasureGroup “Sales Orders”`  
  
 このコマンドは、2001、2002、および 2003 のパーティションを 2004 のパーティションにマージした後、以前の年のパーティションを削除します。  
  
## 参照  
 [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md)   
 [PowerShell を使用したテーブル モデルの管理](http://go.microsoft.com/fwlink/?linkID=227685)  
  
  