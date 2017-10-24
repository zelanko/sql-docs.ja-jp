---
title: "構成設定のリファレンス (Power Pivot for SharePoint) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b57dd3f-7820-4ba8-b233-01dc68908273
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a4f3b5a6b1a90d22889c4cd935abaf94f5172cfd
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="configuration-setting-reference-power-pivot-for-sharepoint"></a>構成設定のリファレンス (Power Pivot for SharePoint)
  このトピックでは、SharePoint ファームの [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションで使用される構成設定に関するリファレンス ドキュメントを提供します。 PowerShell スクリプトを使用してサーバーを構成している場合や、特定の設定に関する情報を必要としている場合は、このトピックの詳細な説明を参照してください。  
  
 構成設定は、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションごとに設定します。 ファーム内で、同じ物理サービス インスタンスの独立した複数の論理インスタンスを構成する手段として、複数のサービス アプリケーションを作成できます。 構成設定は、構成するサービス アプリケーションごとに作成される [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] アプリケーション データベースに格納されます。  
  
 構成設定を変更した場合、その変更は直ちに処理され、それ以降の要求や接続に使用されます。 進行中の操作には、その操作が開始されたときに有効であった設定が適用されます。  
  
 構成に関する特定の領域については、次のリンクをクリックしてください。  
  
 [データ読み込みのタイムアウト](#LoadingData)  
  
 [接続プール](#ConnectionPool)  
  
 [負荷分散](#AllocationScheme)  
  
 [データ更新](#DataRefresh)  
  
 [使用状況データ収集](#UsageData)  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションを作成する方法の手順については、 [「サーバーの全体管理での Power Pivot サービス アプリケーションの作成および構成」](../../analysis-services/power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca.md)を参照してください。  
  
##  <a name="LoadingData"></a> データ読み込みのタイムアウト  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データは、ファームの Analysis Services サーバー インスタンスによって取得され、読み込まれます。 いつどのようにデータに最後にアクセスしたかに応じて、コンテンツ ライブラリか、ローカル ファイル キャッシュから、データが読み込まれます。 データは、クエリ要求または処理要求を受け取るたびにメモリに読み込まれます。 サーバー全体の可用性を最大にするために、割り当てられた時間内にデータの読み込み要求を完了できない場合はその要求を停止するようにサーバーに指示するタイムアウト値を設定できます。  
  
|名前|既定値|有効な値|Description|  
|----------|-------------|------------------|-----------------|  
|データ読み込みのタイムアウト|1800 (秒)|1 ～ 3600|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションが特定の Analysis Services サーバー インスタンスからの応答を待機する時間を指定します。<br /><br /> 既定では、サービス アプリケーションは、特定の要求の転送先となったエンジン サービス インスタンスからのデータ ペイロードを 30 分間待機します。<br /><br /> この時間内に [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ ソースを読み込むことができない場合、そのスレッドは停止され、新しいスレッドが開始されます。|  
  
##  <a name="ConnectionPool"></a> 接続プール  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションでは、接続を再利用できるように、接続プールを作成して管理します。 2 種類の接続プールがあり、1 つは読み取り専用データに対するデータ接続用で、もう 1 つはサーバー接続用です。  
  
 データ接続プールには、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ ソースのキャッシュされた接続が含まれます。 各接続プールは、データベースが読み込まれたときに設定されたコンテキストに基づきます。 このコンテキストには、物理サービス インスタンスの ID、データベース ID、およびデータを要求している SharePoint ユーザーの ID が含まれます。 組み合わせごとに個別の接続プールが作成されます。 たとえば、同じサーバー上で実行されている同じデータベースの異なるユーザーからの要求では、異なるプールの接続が使用されます。  
  
 接続プールの目的は、同じ SharePoint ユーザーによる同じ Analysis Services データベースに対する読み取り専用の要求には、キャッシュされた接続を使用することです。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス インスタンスは、データがメモリに読み込まれるサーバーです。 データベース ID は、データ モデルのインメモリ データ構造体の内部識別子です (モデルは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] キューブ データベースとしてインスタンス化されます)。 この識別子にはバージョン情報が暗黙的に組み込まれます。  
  
 サーバー接続プールには、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション インスタンスから Analysis Services サーバー インスタンスへのキャッシュされた接続が含まれます。この場合、サービス アプリケーションは Analysis Services サーバーに対する [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Sysadmin 権限を使用して接続します。 これらの接続は、データベースの読み込み要求の発行やシステムの状態の監視に使用されます。  
  
 それぞれの種類の接続プールには、接続の管理上、システム メモリを最適に使用するために設定できる上限があります。  
  
|名前|既定値|有効な値|Description|  
|----------|-------------|------------------|-----------------|  
|接続プールのタイムアウト|1800 (秒)|1 ～ 3600|この設定はデータ接続プールに適用されます。<br /><br /> 接続プールでアイドル状態の接続が削除されるまでの時間を指定します。<br /><br /> 既定では、接続は非アクティブな状態が 5 分を超えるとサービス アプリケーションによって削除されます。|  
|ユーザー接続プールの最大サイズ|1000|-1、0、または 1 ～ 10000<br /><br /> -1 を指定した場合、アイドル状態の接続数に制限はありません。<br /><br /> 0 を指定した場合、アイドル状態の接続は一切保持されません。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ ソースへの新しい接続を毎回作成する必要があります。|この設定は、特定の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション インスタンスに対して作成されたすべてのデータ接続プールにおけるアイドル状態の接続数に適用されます。<br /><br /> SharePoint ユーザー、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ、およびサービス インスタンスの一意の組み合わせに対して、個別の接続プールが作成されます。 さまざまな [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ ソースに多数のユーザーがアクセスする場合、接続プールのサイズを大きくすると、サーバーのパフォーマンスが向上することがあります。<br /><br /> [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス インスタンスへのアイドル状態の接続数が 100 を超えると、新たなアイドル状態の接続はプールに返されずに切断されます。|  
|管理接続プールの最大サイズ|200|-1、0、または 1 ～ 10000<br /><br /> -1 を指定した場合、アイドル状態の接続数に制限はありません。|Analysis Services サーバー インスタンスへの [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション接続に対して作成されたすべての管理接続プールにおけるアイドル状態のサーバー接続の最大数。 サーバー接続は、データベースを読み込む場合や SharePoint データベースに変更を保存する場合の要求に使用されます。|  
  
##  <a name="AllocationScheme"></a> 負荷分散  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービスが実行する機能の 1 つは、使用可能な [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス インスタンスのうち、どこに Analysis Services データを読み込むかを決定することです。 **AllocationMethod** の設定は、どのサービス インスタンスが選択されるかに対する条件を指定します。  
  
|名前|既定値|有効な値|Description|  
|----------|-------------|------------------|-----------------|  
|割り当て方法|RoundRobin|ラウンド ロビン<br /><br /> ヘルス ベース|2 つ以上の Analysis Services サーバー インスタンス間で読み込み要求を割り当てる方式。<br /><br /> 既定では、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービスは、サーバーの状態に応じて要求を振り替えます。 ヘルス ベースでは、使用可能なメモリおよび CPU 使用率に基づいて、使用できるシステム リソースが最も多いサーバーに要求が割り当てられます。<br /><br /> ラウンド ロビンでは、現在の読み込みの状態やサーバーの状態に関係なく、使用可能なサーバーに順番に要求が割り振られます。|  
  
##  <a name="DataRefresh"></a> データ更新  
 組織の通常の営業時間を定義する時間の範囲を指定します。 これらの構成設定は、データ更新操作で営業時間後のデータ処理を行うタイミングを決定します。 営業時間後の処理は、営業時間の終了時刻に開始できます。 営業時間後の処理は、通常の営業時間中に生成されたトランザクション データによる [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ ソースの更新を必要とするドキュメント所有者に対するスケジュール オプションです。  
  
|名前|既定値|有効な値|Description|  
|----------|-------------|------------------|-----------------|  
|[開始時刻]|午前 04 時 00 分|有効な範囲は、1 ～ 12 時の範囲の有効な整数です。<br /><br /> 型は Time です。|営業時間の範囲の下限を設定します。|  
|[終了時刻]|午後 08 時 00 分|有効な範囲は、1 ～ 12 時の範囲の有効な整数です。<br /><br /> 型は Time です。|営業時間の範囲の上限を設定します。|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 自動データ更新アカウント|なし|対象アプリケーション ID|このアカウントは、スケジュールの所有者に代わってデータ更新ジョブを実行するために使用します。<br /><br /> 自動データ更新アカウントをサービス アプリケーションの構成ページで参照するには、あらかじめ定義しておく必要があります。 詳細については、 [「PowerPivot 自動データ更新アカウントの構成 (PowerPivot for SharePoint)」](http://msdn.microsoft.com/en-us/81401eac-c619-4fad-ad3e-599e7a6f8493)を参照してください。|  
|ユーザーによるカスタムの Windows 資格情報の入力を許可する|有効|ブール値|スケジュールの所有者が Windows ユーザー アカウントとパスワードを指定してデータ更新ジョブを実行できるようにするオプションを定期データ更新の構成ページに表示するかどうかを指定します。<br /><br /> このオプションを使用するには、Secure Store Service を有効にする必要があります。 詳細については、 [「PowerPivot データ更新用の保存された資格情報の構成 (PowerPivot for SharePoint)」](http://msdn.microsoft.com/en-us/987eff0f-bcfe-4bbd-81e0-9aca993a2a75)を参照してください。|  
|処理履歴の最大の長さ|365|1 ～ 5000 日|データ更新履歴を [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション データベースに保持しておく期間を指定します。 詳細については、「 [Power Pivot Usage Data Collection](../../analysis-services/power-pivot-sharepoint/power-pivot-usage-data-collection.md)」を参照してください。|  
  
##  <a name="UsageData"></a> 使用状況データ収集  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 管理ダッシュボードに表示される使用状況レポートは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]対応のブックの使用方法に関する重要な情報を提供できます。 次の構成設定は、使用状況またはアクティビティ レポートに示される [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サーバー イベントの使用状況データ収集の各側面を制御します。  
  
|名前|既定値|有効な値|Description|  
|----------|-------------|------------------|-----------------|  
|クエリをレポートする間隔|300 (秒)|1 ～ n 秒 (n は任意の有効な整数)。|使用状況データ収集によってファームのデータ転送容量が過度に消費されないようにするため、接続ごとにクエリ統計情報が収集され、単一のイベントとしてレポートされます。 [クエリをレポートする間隔] は、イベントがレポートされる頻度を指定します。 既定では、クエリ統計情報は 5 分おきにレポートされます。<br /><br /> 接続は要求が送信されるとすぐに閉じられるので、1 人のユーザーが 1 つの [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ ソースにアクセスする場合でも、非常に多数の接続が生成されます。 このため、接続が一度作成されたら、同じデータに対する同じユーザーがその接続を再利用できるように、ユーザーと [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ ソースの組み合わせごとに接続プールが作成されます。 定期的に、この構成設定で指定した間隔で、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションによって接続プールの接続ごとに使用状況データがレポートされます。<br /><br /> このレポート間隔の値を大きくすると、ログに記録されるイベントが少なくなります。 ただし、値を大きくしすぎると、サーバーが再起動した場合や接続が閉じられた場合に、イベント データが失われることがあります。<br /><br /> この値を小さくすると、頻度が高くなることでログに記録されるイベントが多くなり、SharePoint の使用状況データベースのデータ コレクション システムに追加される [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]関連の使用状況データが増加します。<br /><br /> 通常は、特定の問題 ( [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 使用状況データが原因で使用状況データベースが急激に大きくなっている場合など) を解決しようとしている場合を除き、この構成設定は変更しないでください。|  
|使用状況データ履歴|365 (日)|0、または 1 ～ n 日 (n は任意の有効な整数)。<br /><br /> 0 を指定した場合、履歴は常に保持され、削除されません。|既定では、使用状況データは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション データベースに 1 年間保存されます。 1 年を経過したレコードはデータベースから削除されます。<br /><br /> 期限切れの履歴データのチェックは、Microsoft SharePoint Foundation の使用状況データ処理ジョブが実行されるときに、毎日行われます。 このタイマー ジョブは、この設定を読み取り、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション データベース内にある期限切れの履歴に対してデータ削除コマンドを起動します。|  
|簡易応答の上限|500 (ミリ秒単位)|1 ～ n ミリ秒 (n は任意の有効な整数)。|既定では、簡易要求のしきい値は 0.5 秒です。<br /><br /> 簡易要求としては、サーバーの ping、メタデータに対する要求、セッションの開始があります。|  
|迅速な応答の上限|1000 (ミリ秒単位)|1 ～ n ミリ秒 (n は任意の有効な整数)。|既定では、迅速な要求のしきい値は 1 秒です。<br /><br /> 迅速な要求は、非常に小さいデータセットを持つ要求、または多数のメンバー セットにまたがるメタデータに対する要求です。|  
|[想定される応答の上限]|3000 (ミリ秒単位)|1 ～ n ミリ秒 (n は任意の有効な整数)。|既定では、想定される要求のしきい値は 3 秒です。<br /><br /> このしきい値は想定されるクエリ時間の上限を設定します。|  
|長い応答の上限|10,000 (ミリ秒)|1 ～ n ミリ秒 (n は任意の有効な整数)。|既定では、長い要求のしきい値は 10 秒です。<br /><br /> 長い要求は、想定よりも長い時間実行されるが許容範囲内である要求です。|  
  
## <a name="see-also"></a>参照  
 [「サーバーの全体管理での Power Pivot サービス アプリケーションの作成および構成」](../../analysis-services/power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca.md)   
 [SharePoint 2010 での PowerPivot データの更新](http://msdn.microsoft.com/en-us/01b54e6f-66e5-485c-acaa-3f9aa53119c9)   
 [使用状況データ収集の構成 &#40;対象は Power Pivot for SharePoint](../../analysis-services/power-pivot-sharepoint/configure-usage-data-collection-for-power-pivot-for-sharepoint.md)   
 [Power Pivot サービス アカウントの構成](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts.md)   
 [Power Pivot 管理ダッシュボードと使用状況データ](../../analysis-services/power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md)  
  
  

