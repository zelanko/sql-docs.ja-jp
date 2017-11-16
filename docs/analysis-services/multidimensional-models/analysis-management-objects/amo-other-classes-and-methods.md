---
title: "AMO の他のクラスとメソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- restores [AMO]
- AMO, backup and restore
- capture logs [AMO]
- AmoException class [AMO]
- Analysis Management Objects, backup and restore
- assembly objects [AMO]
- traces [AMO]
- backups [AMO]
ms.assetid: 60ed5cfa-3a03-4161-8271-0a71a3ae363b
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: aca3ce3e5c98db0c60ca2ae03d7de15283b28f6b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="amo-other-classes-and-methods"></a>AMO のその他のクラスとメソッド
  このセクションには、OLAP またはデータ マイニングに限定されないことと、管理でオブジェクトの管理に役立つ、共通のクラスが含まれています。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。 これらのクラスは、ストアド プロシージャ、トレース、例外、およびバックアップと復元などの機能を対象としています。  
  
 このトピックには、次のセクションが含まれます。  
  
-   [アセンブリ オブジェクト](#Assembly)  
  
-   [バックアップと復元方法](#Backup)  
  
-   [トレース オブジェクト](#Traces)  
  
-   [CaptureLog クラスと CaptureXML 属性](#CaptureLog)  
  
-   [AMOException 例外クラス](#AMO)  
  
 次の図は、このトピックで説明するクラスの関係を示しています。  
  
 ![AMO クラスの他の](../../../analysis-services/multidimensional-models/analysis-management-objects/media/amo-otherclasses.gif "AMO の他のクラス")  
  
##  <a name="Assembly"></a>アセンブリ オブジェクト  
 <xref:Microsoft.AnalysisServices.Assembly> オブジェクトを作成するには、サーバーのアセンブリ コレクションに新しいオブジェクトを追加した後、Update メソッドを使用して、サーバー上で <xref:Microsoft.AnalysisServices.Assembly> オブジェクトを更新します。  
  
 <xref:Microsoft.AnalysisServices.Assembly> オブジェクトを削除するには、<xref:Microsoft.AnalysisServices.Assembly> オブジェクトの Drop メソッドを使用してこれを削除する必要があります。 データベースのアセンブリのコレクションから <xref:Microsoft.AnalysisServices.Assembly> オブジェクトを削除しても、そのアセンブリはアプリケーションを次回実行するまで見えなくなるだけで、削除されません。  
  
 メソッドおよび使用可能なプロパティの詳細については、次を参照してください。<xref:Microsoft.AnalysisServices.Assembly>で<xref:Microsoft.AnalysisServices>です。  
  
> [!IMPORTANT]  
>  COM アセンブリにより、セキュリティ上のリスクが生じる可能性があります。 このリスクやその他の考慮事項により、 [!INCLUDE[ssASversion10](../../../includes/ssasversion10-md.md)]では、COM アセンブリが推奨されていません。 COM アセンブリは、今後のリリースではサポートされない可能性があります。  
  
##  <a name="Backup"></a>バックアップと復元方法  
 Backup と Restore は、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データベースをコピーし、そのコピーを使用してデータベースを復旧するためのメソッドです。 Backup メソッドは <xref:Microsoft.AnalysisServices.Database> オブジェクトに属し、Restore メソッドは <xref:Microsoft.AnalysisServices.Server> オブジェクトに属します。  
  
 データベースのバックアップの実行を許可されているのは、サーバーおよびデータベースの管理者だけです。 バックアップ元とは別のサーバー上にデータベースを復元できるのは、サーバー管理者だけです。 データベース管理者は、自分が所有しているデータベースについてのみ、そのデータベースを上書きすることによってデータベースを復元できます。 元のセキュリティ定義を使用してデータベースを復元した場合、データベース管理者が復元後のデータベースにアクセスできなくなる可能性があります。  
  
 データベース バックアップ ファイルには、.abf 拡張子を付ける必要があります。  
  
### <a name="backup-method"></a>Backup メソッド  
 データベースをバックアップするには、データベース オブジェクトの Backup メソッドを使用します。その際、バックアップ ファイルの名前をパラメーターとして指定します。  
  
##### <a name="default-values"></a>既定値:  
 AllowOverwrite =**false**  
  
 BackupRemotePartitions =**false**  
  
 セキュリティ =**CopyAll**  
  
 ApplyCompression =**は true。**  
  
### <a name="restore-method"></a>Restore メソッド  
 データベースをサーバーに復元するには、パラメーターとしてバックアップ ファイルを指定し、サーバーの Restore メソッドを実行します。  
  
##### <a name="default-values"></a>既定値:  
 AllowOverwrite =**false**  
  
 DataSourceType =**リモート**  
  
 セキュリティ =**CopyAll**  
  
##### <a name="restrictions"></a>制限  
  
1.  ローカル パーティションは、リモート パーティションとして復元することはできません。  
  
2.  リモート パーティションは、ローカル パーティションとして復元することはできません。ただし、リモート パーティションがバックアップされた際のバックアップ元とは異なるサーバー上に復元する場合は、復元可能です。  
  
### <a name="common-parameters-and-properties-for-backup-and-restore-methods"></a>Backup メソッドと Restore メソッドに共通のパラメーターとプロパティ  
  
-   **ファイル**に/から (UNC 名) をバックアップするファイルの名前です。  
  
-   **場所**などの特定のサーバー バックアップの情報を指定**BackupFile**です。これにより、リモート データベースの個別のバックアップ ファイルを指定できます。  
  
-   **DatasourceID**リモート サーバーにおける下位データベースの ID を指定します。  
  
-   **ConnectionString**リモート サーバーが変更された場合は、リモート データ ソースを調整することができます。 DatasourceID は、ConnectionString が存在する場合は常に指定する必要があります。  
  
-   **フォルダー**により、ローカル ハード ドライブ上のパーティションに対してフォルダーを再マップ  
  
-   **元**ローカル パーティションに対する元のフォルダーです。  
  
-   **新しい**新しい場所はローカル パーティションの対応する '元の' 古いフォルダー内に存在するために使用します。  
  
-   **パスワード**空白でないこと、サーバーは、バックアップ ファイルの暗号化を指定する場合は、します。  
  
##  <a name="Traces"></a>トレース オブジェクト  
 Trace は、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンスを監視、再生、管理するためのフレームワークです。 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] などのクライアント アプリケーションはトレースをサブスクライブし、サーバーはトレース定義での指定に従ってトレース イベントを返します。  
  
 各イベントは、イベント クラスによって記述されます。 イベント クラスは生成されたイベントの種類を記述します。 イベント クラス内では、イベントのサブクラスによって、より詳細なレベルの分類が記述されます。 各イベントは、多くの列によって記述されます。 トレース イベントを記述する列は、すべてのイベントに対して一貫しており、SQL トレースの構造に準拠しています。 各列に記録される情報は、イベント クラスに応じて異なる可能性があります。つまり、定義済みの列のセットは各トレースに対して定義されますが、列の意味はイベント クラスに応じて異なる可能性があります。 たとえば、TextData 列は、すべてのステートメント イベントに対する元の ASSL を記録するために使用されます。  
  
 トレース定義には、トレースされるイベント クラスを 1 つ以上同時に含めることができます。 各イベント クラスについて、トレース定義に 1 つ以上のデータ列を追加できますが、すべてのトレース列を使用する必要はありません。 データベース管理者は、使用できる列のうちどれをトレース内に含めるかを決定できます。 さらに、イベント クラスは、トレース内の任意の列に対するフィルターの条件に基づいて選択的にトレースできます。  
  
 トレースは、開始および削除できます。 複数のトレースを任意のタイミングで一度に実行できます。 トレース イベントは、実行中にキャプチャしたり、後から分析または再生するためにファイルに送信することができます。 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] は、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] トレース イベントを分析および再生するためのツールです。 同じトレースからイベントを受け取るために、複数の接続を使用できます。  
  
 トレースは、サーバー トレースとセッション トレースの 2 つのグループに分けられます。 サーバー トレースは、サーバー内のすべてのイベントについて通知します。セッション トレースは、現在のセッション内のイベントについてのみ通知します。  
  
 サーバーのトレース コレクションからのトレースは、次の方法で定義します。  
  
1.  <xref:Microsoft.AnalysisServices.Trace> オブジェクトを作成し、トレース ID、名前、ログ ファイル名、追加と上書きのどちらを実行するかなどの基本データを設定します。  
  
2.  トレース オブジェクトの Events コレクションに、監視する Events を追加します。 各イベントに対して、データ列が追加されます。  
  
3.  不要なデータの行を除外するために、それらの不要なデータの行をフィルター コレクションに追加してフィルターを設定します。  
  
4.  トレースを開始します。トレースを作成しても、データの収集は開始されません。  
  
5.  トレースを停止します。  
  
6.  [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] を使用してトレース ファイルを確認します。  
  
 セッション オブジェクトによるトレースを取得する方法は次のとおりです。  
  
1.  アプリケーションで、SessionTrace によって生成されたトレース イベントを処理するための関数を定義します。 使用できるイベントは OnEvent と Stopped です。  
  
2.  定義した関数をイベント ハンドラーに追加します。  
  
3.  セッション トレースを開始します。  
  
4.  プロセスを実行し、関数ハンドラーにイベントをキャプチャさせます。  
  
5.  セッション トレースを停止します。  
  
6.  アプリケーションを続行します。  
  
##  <a name="CaptureLog"></a>CaptureLog クラスと CaptureXML 属性  
 AMO によって実行されるすべてのアクションは、XMLA メッセージとしてサーバーに送信されます。 AMO によって、SOAP ヘッダーを持たないこれらのメッセージをすべてキャプチャする手段が提供されます。 詳細については、次を参照してください。 [AMO クラスの導入](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)です。 CaptureLog は、オブジェクトと操作をスクリプト出力するための AMO 内のメカニズムです。オブジェクトと操作のスクリプトは XMLA で作成されます。  
  
 CaptureXML サーバー オブジェクトのプロパティを XML のキャプチャを開始するに設定する必要があります**true**です。 その後、サーバーに送信されるすべてのアクションが、サーバーに送信されることなく、CaptureLog クラスでキャプチャされるようになります。 CaptureLog にはキャプチャ ログを消去するために使用する Clear メソッドがあるため、CaptureLog はクラスと見なされます。  
  
 ログを読み取るには、文字列コレクションを取得し、それらの文字列の反復処理を開始します。 また、サーバー オブジェクト メソッド ConcatenateCaptureLog を使用して、すべてのログを 1 つの文字列に連結することもできます。 ConcatenateCaptureLog には、3 つのパラメーターがあり、そのうち 2 つは必須です。 必要なパラメーターが*トランザクション*のブール型、および*並列*、ブール型のです。 場合*トランザクション*に設定されている**true**、各コマンドの中ではなく、単一のトランザクションが個別のトランザクションとして扱われる XML バッチ ファイルが作成されることを示します。 場合*並列*に設定されている**true**、記録されたと、バッチ ファイル内のすべてのコマンドは順番にではなく、同時実行記録することを示します。  
  
##  <a name="AMO"></a>AMOException 例外クラス  
 AMOException 例外クラスを使用して、AMO によってスローされるアプリケーション内の例外を簡単にキャッチできます。  
  
 AMO は、さまざまな問題が検出されるたびに例外をスローします。 次の表は、AMO によって処理される例外の種類を示しています。 例外は <xref:Microsoft.AnalysisServices.AmoException> クラスから派生します。  
  
|例外|発生元|Description|  
|---------------|------------|-----------------|  
|<xref:Microsoft.AnalysisServices.AmoException>|基本クラス|必要な親オブジェクトが見つからない場合、または必要なアイテムがコレクション内で見つからない場合に、アプリケーションはこの例外を受け取ります。|  
|<xref:Microsoft.AnalysisServices.OutOfSyncException>|AMOException から派生|AMO がエンジンに同期されておらず、AMO が認識していないオブジェクト参照をエンジンが返す場合、アプリケーションはこの例外を受け取ります。|  
|<xref:Microsoft.AnalysisServices.OperationException>|AMOException から派生|これは、アプリケーションが頻繁に受け取る重要な例外です。 この例外には、サーバーから発生するエラーの詳細が含まれています。このエラーの原因としては、更新、処理、削除などの不正な AMO 操作が考えられます。|  
|<xref:Microsoft.AnalysisServices.ResponseFormatException>|AMOException から派生|この例外は、AMO によって認識されない形式のメッセージをエンジンが返す場合に発生します。|  
|<xref:Microsoft.AnalysisServices.ConnectionException>|AMOException から派生|この例外は、(Server.Connect を使用して) 接続を確立できない場合、または AMO がエンジンと通信している間 (更新、処理、または削除の間など) に接続が失われる場合に発生します。|  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices>   
 [AMO クラスの概要](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [論理アーキテクチャと #40 です。Analysis Services - 多次元データ &#41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [データベース オブジェクト & #40 です。Analysis Services - 多次元データ &#41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  

