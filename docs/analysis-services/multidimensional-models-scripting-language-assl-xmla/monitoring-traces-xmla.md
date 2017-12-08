---
title: "トレースの監視 (XMLA) |Microsoft ドキュメント"
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
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- XML for Analysis, traces
- XMLA, traces
- monitoring traces [XMLA]
- traces [Analysis Services]
ms.assetid: cdbfb984-18bd-4c4e-8fb7-d64ce298ed35
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 45bf2482dc80a7f6f2019572ffd38b1937e72b85
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="monitoring-traces-xmla"></a>トレースの監視 (XMLA)
  使用することができます、[購読](../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md)XML for Analysis (XMLA) のインスタンスで定義されている既存のトレースを監視するコマンド[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]です。 **購読**コマンドが行セットとしてトレースの結果を返します。  
  
## <a name="specifying-a-trace"></a>トレースの指定  
 [オブジェクト](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)のプロパティ、**購読**コマンドは、いずれかへのオブジェクト参照を含める必要があります、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンスまたは上のトレース、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンス。 場合、**オブジェクト**プロパティが指定されていない、またはトレース識別子が指定されていない、**オブジェクト**、プロパティ、**購読**コマンドの既定のセッション トレースを監視します。コマンドの SOAP ヘッダーで指定された明示的なセッションです。  
  
## <a name="returning-results"></a>結果の返送  
 **購読**コマンドは、指定されたトレースでキャプチャされたトレース イベントを含む行セットを返します。 **購読**によって、コマンドが取り消されるまで、コマンドはトレース結果を返します、[キャンセル](../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)コマンド。  
  
 行セットに含まれる列は、次の表のとおりです。  
  
|列|データ型|Description|  
|------------|---------------|-----------------|  
|EventClass|Integer|トレースによって受信されたイベントのイベント クラス。|  
|EventSubclass|Long integer|トレースによって受信されたイベントのイベント サブクラス。|  
|CurrentTime|DateTime|イベントの開始時刻 (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|StartTime|DateTime|イベントの開始時刻 (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|EndTime|DateTime|イベントの終了時刻 (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。<br /><br /> プロセスまたはアクションの開始を記述するイベント クラスの場合、この列は設定されません。|  
|Duration|Long integer|イベントで経過した時間の合計 (ミリ秒単位)。|  
|CPUTime|Long integer|イベントで経過したプロセッサ時間 (ミリ秒単位)。|  
|JobID|Long integer|プロセスのジョブ識別子。|  
|SessionID|文字列|イベントが発生したセッションの識別子。|  
|SessionType|文字列|イベントが発生したセッションの種類。|  
|ProgressTotal|Long integer|イベントによって報告された進行状況の総数または量。|  
|IntegerData|Long integer|イベントに関連付けられている整数データ。 この列の内容は、イベント クラス、およびイベントのサブクラスによって異なります。|  
|ObjectID|文字列|イベントが発生したオブジェクトの識別子。|  
|ObjectType|文字列|ObjectName で指定されたオブジェクトの種類。|  
|ObjectName|文字列|イベントが発生したオブジェクトの名前。|  
|ObjectPath|文字列|イベントが発生したオブジェクトの階層パス。 パスは、ObjectName で指定されたオブジェクトの親に関するオブジェクト識別子の、コンマ区切りの文字列として表されます。|  
|ObjectReference|文字列|ObjectName で指定されたオブジェクトへのオブジェクト参照を表す XML 表現。|  
|NestLevel|Integer|イベントが発生したトランザクションのレベル。|  
|NumSegments|Long integer|イベントが発生したコマンドによって影響を受ける、またはアクセスされるデータ セグメントの数。|  
|Severity|Integer|イベントの例外の重大度レベル。 この列には、以下の値のいずれかが含まれます。<br /><br /> <br /><br /> 0: 成功<br /><br /> <br /><br /> 1: 情報<br /><br /> <br /><br /> 2: 警告<br /><br /> <br /><br /> 3: エラー|  
|Success|ブール値|コマンドが成功したか、失敗したかを示します。|  
|[エラー]|Long integer|イベントのエラー番号 (ある場合)。|  
|ConnectionID|文字列|イベントが発生した接続の識別子。|  
|DatabaseName|文字列|イベントが発生したデータベースの名前。|  
|NTUserName|文字列|イベントに関連付けられているユーザーの Windows ユーザー名。|  
|NTDomainName|文字列|イベントに関連付けられているユーザーの Windows ドメイン。|  
|ClientHostName|文字列|クライアント アプリケーションが実行されているコンピューターの名前。 この列には、クライアント アプリケーションによって渡された値が格納されます。|  
|ClientProcessID|Long integer|クライアント アプリケーションのプロセス識別子。|  
|ApplicationName|文字列|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスへの接続を作成したクライアント アプリケーションの名前。 この列には、プログラムの表示名ではなく、クライアント アプリケーションによって渡された値が格納されます。|  
|NTCanonicalUserName|文字列|イベントに関連付けられているユーザーの Windows の正規のユーザー名。|  
|SPID|文字列|イベントが発生したセッションのサーバー プロセス ID (SPID)。 この列の値は、イベントが発生した XMLA メッセージの SOAP ヘッダーで指定されたセッション ID に直接対応します。|  
|TextData|文字列|イベントに関連付けられたテキスト データです。 この列の内容は、イベント クラス、およびイベントのサブクラスによって異なります。|  
|ServerName|文字列|イベントが発生した [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの名前。|  
|RequestParameters|文字列|イベントが発生したパラメーター化クエリまたは XMLA コマンドのパラメーター。|  
|RequestProperties|文字列|イベントが発生した XMLA メソッドのプロパティ。|  
  
## <a name="see-also"></a>参照  
 [Analysis Services での XMLA による開発](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
