---
title: "RDS プログラミング モデルの詳細 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RDS programming model [ADO], details
ms.assetid: 3e57af8d-519b-4467-a0bd-af468534cefd
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: db8a1222c560b54629baa34da595e0f5c49835b0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="rds-programming-model-in-detail"></a>RDS プログラミング モデルの詳細
RDS のプログラミング モデルの主要な要素を次に示します。  
  
-   RDS.DataSpace  
  
-   RDSServer.DataFactory  
  
-   RDS.DataControl  
  
-   イベント  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="rdsdataspace"></a>RDS.DataSpace  
 クライアント アプリケーションには、サーバーと呼び出すサーバー プログラムを指定する必要があります。 代わりに、アプリケーションでは、サーバー プログラムへの参照を受け取るし、サーバー プログラム自体の場合と同様に参照を扱うことができます。  
  
 RDS オブジェクト モデルを使用してこの機能を具体化する、 [.rds ですDataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md)オブジェクト。  
  
 サーバーのプログラムは、識別子に指定された、プログラム、または*ProgID*です。 サーバーを使用して、 *ProgID*およびサーバー コンピューターのレジストリを実際に起動するプログラムに関する情報を検索します。  
  
 RDS は、インターネットまたはイントラネット; 経由でリモート サーバーでサーバー プログラムがあるかによって内部的に区別ローカル エリア ネットワーク; 上のサーバーまたは、サーバーではなくが、代わりにローカルのダイナミック リンク ライブラリ (DLL) にします。 この区別は、情報がクライアントとサーバー間で交換され、クライアント アプリケーションに返される参照の型で明確に区別方法を決定します。 ただしの観点から、この区別がない特殊な意味します。 自分にとって重要なすべてが使用可能なプログラムの参照を受け取ります。  
  
## <a name="rdsserverdatafactory"></a>RDSServer.DataFactory  
 RDS にデータ ソースと戻り値に対して SQL クエリを実行できるか、既定のサーバー プログラムは、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトか、**レコード セット**オブジェクトし、データ ソースを更新します。  
  
 RDS オブジェクト モデルを使用してこの機能を具体化する、 [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)オブジェクト。  
  
 さらに、このオブジェクトには、空の作成方法の**Recordset**プログラムで満たすことができるオブジェクト ([CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md))、および変換するための別の方法、**レコード セット**を Web ページを構築するテキスト文字列にオブジェクト ([ConvertToString](../../../ado/reference/rds-api/converttostring-method-rds.md))。  
  
 一部の標準の接続のコマンドの動作をオーバーライドする ado、 **RDSServer.DataFactory**で、 **DataFactory**ハンドラーとカスタマイズを含むファイル接続、コマンド、およびセキュリティ パラメーター。  
  
 サーバー プログラムと呼ぶことが、*ビジネス オブジェクト*です。 複雑なデータ アクセス、有効性チェックを実行できる、独自のカスタム ビジネス オブジェクトを記述することができます。 インスタンスを作成するには、カスタム ビジネス オブジェクトを記述する場合でも、 **RDSServer.DataFactory**オブジェクトをそのメソッドの一部を使用して、独自のタスクを実行します。  
  
## <a name="rdsdatacontrol"></a>RDS.DataControl  
 RDS の機能を結合する手段を提供する、 **.rds ですDataSpace**と**RDSServer.DataFactory**も簡単に使用するビジュアル コントロールを有効にして、 **Recordset**データ ソースからクエリによって返されるオブジェクト。 RDS を自動的にサーバー上の情報にアクセスして、ビジュアル コントロールで表示可能な限り行うには、最も一般的なケースを試行します。  
  
 RDS オブジェクト モデルを使用してこの機能を具体化する、 [.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクト。  
  
 **.Rds ですDataControl**は 2 つの特徴があります。 1 つの側面は、データ ソースに関連します。 コマンドと接続情報を使用して設定した場合、**接続**と**SQL**のプロパティ、 **.rds ですDataControl**が自動的に使用されている、 **.rds ですDataSpace**を既定値への参照を作成する**RDSServer.DataFactory**オブジェクト。 **RDSServer.DataFactory**を使用して、**接続**プロパティの値をデータ ソースへの接続を使用して、 **SQL**プロパティの値を取得する、 **レコード セット**からデータ ソース、および戻り値、 **Recordset**オブジェクトを**.rds ですDataControl**です。  
  
 表示に関連する 2 番目の縦横比返された**Recordset**ビジュアル コントロール内の情報です。 コントロールが visual を関連付けることができます、 **.rds ですDataControl** (、プロセスでは、バインディングと呼ばれます) で、関連する情報にアクセスできるように**レコード セット**Microsoft® Internet Explorer で Web ページ上のクエリの結果を表示するオブジェクト。 各**.rds ですDataControl**オブジェクトは 1 つにバインド**Recordset** (たとえば、テキスト ボックス、コンボ ボックス、グリッド コントロールとなど) 1 つまたは複数のビジュアル コントロールへの 1 つのクエリの結果を表すオブジェクト。 1 つ以上あります**.rds ですDataControl**各ページ上のオブジェクト。 各**.rds ですDataControl**オブジェクトが別のデータ ソースに接続することができ、別のクエリの結果は含まれています。  
  
 **.Rds ですDataControl**オブジェクトに移動、並べ替え、および関連付けられている行をフィルター処理用の独自のメソッドもあります**Recordset**オブジェクト。 これらのメソッドと同様に、ADO 上のメソッドとして同じ**Recordset**オブジェクト。  
  
## <a name="events"></a>イベント  
 RDS には、ADO イベント モデルの独立した独自のイベントの 2 つがサポートされています。 [OnReadyStateChange](../../../ado/reference/rds-api/onreadystatechange-event-rds.md)イベントが呼び出されたときに、 **.rds ですDataControl** [ReadyState](../../../ado/reference/rds-api/readystate-property-rds.md)プロパティが変更された、非同期操作が正常に完了したら、通知を終了すると、またはエラーが発生しました。 [OnError](../../../ado/reference/rds-api/onerror-event-rds.md)イベントは、エラーが発生するたびに呼び出されます、非同期操作中にエラーが発生した場合でもです。  
  
> [!NOTE]
>  Microsoft Internet Explorer では、RDS の 2 つの追加イベント:**詳細**、ことを示します、**レコード セット**機能ですが、行を取得するには、 **詳細について**、ことを示します、 **Recordset**行の取得が完了します。  
  
## <a name="see-also"></a>参照  
 [オブジェクトと RDS プログラミング モデル](../../../ado/guide/remote-data-service/rds-programming-model-with-objects.md)   
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [DataFactory オブジェクト (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)   
 [DataSpace オブジェクト (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)   
 [RDS のシナリオ](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [RDS チュートリアル](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [RDS の使用方法とセキュリティ](../../../ado/guide/remote-data-service/rds-usage-and-security.md)




