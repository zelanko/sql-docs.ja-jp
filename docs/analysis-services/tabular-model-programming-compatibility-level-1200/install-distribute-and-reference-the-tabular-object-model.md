---
title: "インストール、配布、および表形式オブジェクト モデルを参照 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: e51769f7-aac7-4835-a5ae-91aac04aa476
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9688a692d25d484b05bca88e0779d2812944f3af
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="install-distribute-and-reference-the-tabular-object-model"></a>インストール、配布、および表形式オブジェクト モデルを参照

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

この記事では、ダウンロード、参照、および Analysis Services 表形式オブジェクト モデル (TOM)、c# ライブラリを作成および表形式モデルとマネージ コード内のデータベースを管理するための再配布する方法について説明します。  
  
TOM は、SQL Server 2016 に付属している AMO クライアント ライブラリ (Microsoft.AnalysisServices.dll) の拡張です。 SQL Server 2016 のリリースでは、表形式メタデータ エンジンを対象とするテーブル モデルで動作します。 TOM を使用するには、モデルとデータベースが互換性レベル 1200 以上でなければなりません。  

## <a name="amo-tom-assemblies"></a>AMO TOM アセンブリ

SQL Server 2016 では、リファクタリングしたし、新しいコア、表形式、および JSON のアセンブリを含めるには AMO を展開します。 元の最初のリリースから Analysis Services の一部となった Microsoft.AnalysisServices.dll AMO アセンブリも含まれています。 再構築された AMO は、1 つのアセンブリへの一般的なクラスの負荷を軽減し、その他のアセンブリを利用して表形式および多次元の Api の間で論理区画を提供します。 

次の表では、各アセンブリについて説明します。
  
アセンブリ  |機能  |重要なクラス |
---------|---------|--------------  |
コア <br/>Microsoft.AnalysisServices.Core.dll | 表形式および多次元データベースの両方に共通します。 <br/><br/>例外処理、Analysis Services インスタンスと、データベースへの汎用的な接続と共通のプロパティとメソッドをサーバーおよびデータベース オブジェクトへのアクセスを提供します。 <br/><br/>SQL Server 2016 を対象とする任意の AMO ソリューションに必須です。 | コア&nbsp;サーバー<br/>コア&nbsp;データベース<br/>AmoException
TOM<br/> Microsoft.AnalysisServices.Tabular.dll、13.0.1601.5 のバージョンまたはそれ以降。| 作成および表形式メタデータ オブジェクトを管理します。 | TOM&nbsp;サーバー <br/>TOM&nbsp;データベース<br /> [モデル]<br /> テーブル<br /> 列<br /> リレーションシップ
  AMO<br /> Microsoft.AnalysisServices.dll| 作成し、テーブル 1050 ~ 1103 データベースを含め、多次元メタデータ オブジェクトを管理します。 | AMO&nbsp;サーバー <br />AMO&nbsp;データベース <br /> Cube <br /> [ディメンション] <br /> [MeasureGroup] 
Json<br/>Microsoft.AnalysisServices.Tabular.Json.dll | Analysis Services のワークロードでの JSON のシリアル化する機能的な変更を導入する際のリスクを削除する更新プログラムを制御する NewtonSoftJson.dll (JSON.NET) をラップする DLL のヘルパーです。 <br /> <br />この DLL は、TOM に依存関係として存在し、コード内で直接使用するものではありません。 | [なし] :  
  
 ### <a name="understanding-assembly-dependencies"></a>アセンブリの依存関係を理解します。
  
AMO プログラミングをするには、ソリューションが依存する Dll への参照を含める必要があります。 TOM と AMO の両方は、基本クラスを提供するため Core に依存します。

AMO は、AMO 内の一部のクラスは、TOM からクラスを参照するために、TOM に依存します。 たとえば、AMO データベース オブジェクトには、プロパティ TOM dll に実装されているモデルの種類のモデルがあります。 

![AMO TOM の依存関係](../../analysis-services/tabular-model-programming-compatibility-level-1200/media/amo-tom-dependencies.png)

Microsoft.AnalysisServices.Tabular.dll、せず Microsoft.AnalysisServices.dll を配布することはできませんが、対応することがなく、他の名前空間を参照することができます。

### <a name="choosing-which-namespace-to-use-in-code"></a>コードで使用する名前空間を選択します。

[オブジェクト階層](../../analysis-services/tabular-model-programming-compatibility-level-1200/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo.md)データベースの下の任意のオブジェクトは、モデル オブジェクトによって表形式のメタデータ構築またはキューブ、ディメンション、または MeasureGroup オブジェクトを使用して多次元メタデータ構築のいずれか。 高度な操作をサーバー、データベース、ロール、またはトレース レベルで、どの名前空間を参照するは異なります、ワークロード、コードの選択をサポートする必要があります。

* Tabular.Server または表形式データベースを使用して、ソリューションが互換性レベル 1200 以上とを操作するデータベース オブジェクトは、モデル、テーブル、列、および表形式のメタデータ構造として表されるその他のオブジェクトにアクセスを提供する必要があります。
* ダウン ストリーム コードは、キューブ、データ ソース、DataSourceViews、およびディメンションなどの多次元オブジェクトを参照している場合は、AnalysisServices.Server または AnalysisServices.Database を使用します。

ツールとさまざまなデータベースやモデルの種類をサポートするアプリケーションの両方の名前空間を必要があります。 

コードでは Core 名前空間の参照は不要です。コアのクラスは、主要なオブジェクトの名前と説明のように、共通のプロパティを提供するために作成される基本クラスです。  
  
## <a name="determine-whether-amo-and-tom-installation-is-required"></a>TOM と AMO のインストールが必要かどうかを判断します。  
   
 AMO および TOM はバンドルとしてまとめ、1 つのクライアント ライブラリでします。 SQL Server 2016 Analysis Services インスタンス、クライアント ライブラリ、または SQL server 2016 インスタンスを対象とする SQL Server Data Tools のバージョンを既にインストールした場合、Microsoft.AnalysisServices.dll が既にインストールされています。  
  
 アセンブリが既にインストールされているかどうかを判断するのには、これらの場所のいずれかを確認します。
* C:\Windows\Microsoft.NET\assembly\GAC_MSIL
* C:\Program files \microsoft SQL server \130\sdk\assemblies にあります。
* C:\Program files \microsoft SQL Server\130\DTS\Tasks
* C:\Program files \microsoft SQL Server\MSAS13 です。MSSQLSERVER\OLAP\bin
 
 次のアセンブリの存在を確認します。
*  Microsoft.AnalysisServices.Core.dll
*  Microsoft.AnalysisServices.dll
*  Microsoft.AnalysisServices.Tabular.dll
*  Microsoft.AnalysisServices.Tabular.Json.dll   
   
## <a name="download-sqlasamo"></a>SQL_AS_AMO をダウンロードします。  
 
 Microsoft.AnalysisServices.dll が NuGet マネージャーを使用して使用できないことに注意してください。
  
1. 移動して[、SQL Server 2016 の Feature Pack のダウンロード ページ](https://www.microsoft.com/download/details.aspx?id=52676)です。  
  
2. **[ダウンロード]**をクリックします。  
  
3. いずれかを選択**\X64\SQL_AS_AMO.msi**または**\X86\SQL_AS_AMO.msi**です。 いずれか 1 つを選択することができます: TOM と AMO のアセンブリは、プラットフォームに依存しません。
  
4. をクリックして**次**ダウンロードを続行します。 .Msi ファイルが表示されます、**ダウンロード**フォルダーです。  
  
## <a name="install-sqlasamo"></a>SQL_AS_AMO をインストールします。  
  
1. ダブルクリックして**SQL_AS_AMO.msi**し、インストールをステップします。  
  
2. 移動して**C:\Program files \microsoft SQL server \130\sdk\assemblies にあります**Microsoft.AnalysisServices.Core.dll、Microsoft.AnalysisServices.dll、Microsoft.AnalysisServices.Tabular.dll の配置を確認し、Microsoft.AnalysisServices.Tabular.Json.dll です。   
  
## <a name="add-references"></a>参照を追加します。  
  
1. **ソリューション エクスプ ローラー** > **参照の追加** > **参照**です。  
2. 移動して**C:\Program files \microsoft SQL server \130\sdk\assemblies にあります**を選択します。  
   * Microsoft.AnalysisServices.Core  
   * Microsoft.AnalysisServices.Tabular  
   * Microsoft.AnalysisSerivces.Tabular.Json  
  
3. **[OK]**をクリックします。  **ソリューション エクスプ ローラー**、[参照] フォルダー、アセンブリが存在することを確認します。
  
4. コード ページを開き、データベースとモデルが 1200 の表形式またはより高い互換性レベルの場合、Microsoft.AnalysisServces.Tabular 名前空間を追加します。 
  
   ```   
   using Microsoft.AnalysisServices; 
   using Microsoft.AnalysisServices.Tabular;
   ```  
    必要に応じて、具体的には SQL Server 2016 を表形式サーバー モードではない Analysis Services のインスタンスへの接続の広範なセットをサポートするために Microsoft.AnalysisServces を追加します。 
 
    サーバー、データベース、ロール、およびトレースのオブジェクトに対して共通のクラスを持つ名前空間を含む、ときに、使用する名前空間を修飾することによりあいまいな参照を回避する (たとえば、Microsoft.AnalysisServices.Tabular.Server をインスタンス化するサーバーオブジェクト テーブルの名前空間を使用)。

## <a name="redistribute-amo-and-tom-with-your-application"></a>AMO および TOM をアプリケーションと共に再配布します。  
  
AMO および TOM の再配布は、使用、 **sql_as_amo.msi**インストール パッケージです。 AMO または TOM を呼び出すクライアント アプリケーションのセットアップ プログラムを作成する場合は追加**sql_as_amo.msi**用の実行可能にします。 これは、AMO と TOM クライアント ライブラリを再配布するためのサポートされている唯一の方法です。  
  
パッケージは自己完結型であり、コードで AMO および TOM を呼び出すために必要なすべてのアセンブリを提供します。 SQL_AS_OLEDB.msi またはある SQL_AS_ADOMD.msi をなど、他のパッケージは、TOM プログラミング シナリオを具体的には必要ではありません。

