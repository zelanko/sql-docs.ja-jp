---
title: '[SSIS ログの構成] ダイアログボックス |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.configuredtslogs.loggingdetails.f1
- sql12.dts.designer.configuredtslogs.providersandlogs.f1
- sql12.dts.designer.configuredtslogs.containers.f1
helpviewer_keywords:
- Configure SSIS Logs dialog box
ms.assetid: 4b980275-cd9a-4943-8c36-727d51f9a484
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 6fab2f2e8fad2cd77e5bc27a78e66940fc40544b
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84921663"
---
# <a name="configure-ssis-logs-dialog-box"></a>[SSIS ログの構成] ダイアログ ボックス
  **SSIS ログの構成]** ダイアログ ボックスを使用して、パッケージのログ記録オプションを定義します。  
  
 **どうしたいんですか。**  
  
1.  [[SSIS ログの構成] ダイアログ ボックスを開く](#open_dialog)  
  
2.  [[コンテナー] ペインでオプションを構成する](#container)  
  
3.  [[プロバイダーとログ] タブでオプションを構成する](#provider)  
  
4.  [[詳細] タブでオプションを構成する](#detail)  
  
##  <a name="open-the-configure-ssis-logs-dialog-box"></a><a name="open_dialog"></a>[SSIS ログの構成] ダイアログボックスを開く  
 **[SSIS ログの構成] ダイアログ ボックスを開くには**  
  
-   [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーで、 **[SSIS]** メニューの **[ログ記録]** をクリックします。  
  
##  <a name="configure-the-options-in-the-containers-pane"></a><a name="container"></a> [コンテナー] ペインでオプションを構成する  
 **[SSIS ログの構成]** ダイアログ ボックスの **[コンテナー]** ペインを使用すると、パッケージおよびパッケージのコンテナーでログを有効できます。  
  
### <a name="options"></a>オプション  
 **Containers**  
 パッケージとパッケージのコンテナーでログを有効にするには、階層ビューのチェック ボックスをオンにします。  
  
-   オフになっている場合、そのコンテナーでログは無効になります。 ログを有効にする場合はオンにします。  
  
-   淡色表示になっている場合、コンテナーは親のログ オプションを使用します。 このオプションは、パッケージには使用できません。  
  
-   オンにすると、コンテナーは固有のログ オプションを定義します。  
  
 コンテナーが淡色表示になっている場合に、そのコンテナーにログ オプションを設定するには、チェック ボックスを 2 回クリックします。 最初のクリックでチェック ボックスがオフになった後、2 番目のクリックでオンになったら、使用するログ プロバイダーを選択し、ログに記録する情報を指定できます。  
  
##  <a name="configure-the-options-on-the-providers-and-logs-tab"></a><a name="provider"></a>[プロバイダーとログ] タブでオプションを構成する  
 **[SSIS ログの構成]** ダイアログ ボックスの **[プロバイダーとログ]** タブを使用すると、ランタイム イベントをキャプチャするログを作成したり構成したりできます。  
  
### <a name="options"></a>オプション  
 **プロバイダー型の**  
 ログ プロバイダーの種類を一覧から選択します。  
  
 **追加**  
 パッケージのログ プロバイダーのコレクションに、指定した種類のログを追加します。  
  
 **名前**  
 **[SSIS ログの構成]** ダイアログ ボックスの **[コンテナー]** ペインで選択したコンテナーまたはタスクについて、ログを有効または無効にします。 [名前] フィールドは編集可能です。 プロバイダーの既定の名前を使用するか、わかりやすい一意な名前を入力します。  
  
 **説明**  
 [説明] フィールドは編集可能です。 クリックして、ログの既定の説明を変更します。  
  
 **構成**  
 既存の接続マネージャーを一覧から選択するか、をクリックして \<**New connection...**> 新しい接続マネージャーを作成します。 ログ プロバイダーの種類によっては、OLE DB 接続マネージャーやファイル接続マネージャーを構成できます。 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows イベント ログ用のログ プロバイダーの場合、接続は不要です。  
  
 関連項目:「 [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md) 」、「 [File Connection Manager](connection-manager/file-connection-manager.md)」  
  
 **削除**  
 ログ プロバイダーを選択して、 **[削除]** をクリックします。  
  
##  <a name="configure-the-options-on-the-details-tab"></a><a name="detail"></a>[詳細] タブでオプションを構成する  
 **[SSIS ログの構成]** ダイアログ ボックスの **[詳細]** タブで、ログ記録を有効にするイベントと、ログ記録する詳細情報を指定します。 選択した情報は、パッケージ内のすべてのログ プロバイダーに適用されます。 たとえば、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスとテキスト ファイルに別々の情報を書き込むことはできません。  
  
### <a name="options"></a>オプション  
 **イベント**  
 イベントのログ記録を有効または無効にします。  
  
 **説明**  
 イベントの説明が表示されます。  
  
 **詳細設定**  
 ログ記録するイベントをオンまたはオフにし、各イベントでログ記録する情報をオンまたはオフにします。 **[標準]** をクリックすると、ログの詳細情報がイベントの一覧を除いてすべて非表示になります。 次の情報をログ記録できます。  
  
|値|説明|  
|-----------|-----------------|  
|**Computer**|ログ記録されたイベントが発生したコンピューターの名前。|  
|**Operator**|パッケージを起動した人物のユーザー名。|  
|**SourceName**|ログ記録されたイベントが発生したパッケージ、コンテナー、またはタスクの名前。|  
|**SourceID**|ログ記録されたイベントが発生したパッケージ、コンテナー、またはタスクの GUID (global unique identifier)。|  
|**ExecutionID**|パッケージ実行インスタンスの GUID。|  
|**[MessageText]**|ログ エントリに関連付けられているメッセージ。|  
|**[DataBytes]**|将来利用するために予約されています。|  
  
 **Basic**  
 ログ記録するイベントをオンまたはオフにします。 イベントの一覧を除いて、ログの詳細情報が非表示になります。 イベントを選択すると、既定でそのイベントのすべてのログ詳細情報が選択されます。 **[詳細設定]** をクリックすると、ログの詳細情報がすべて表示されます。  
  
 **読み込み**  
 ログのオプションを設定するテンプレートとして使用される、既存の XML ファイルを指定します。  
  
 **保存**  
 構成の詳細をテンプレートとして XML ファイルに保存します。  
  
  
