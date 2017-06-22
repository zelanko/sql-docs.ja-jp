---
title: "レポート処理プロパティを設定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- on-demand reports
- report processing [Reporting Services], execution properties
- snapshots [Reporting Services], running reports from
- cached reports [Reporting Services]
- report snapshots [Reporting Services], running reports from
- report execution snapshots [Reporting Services]
ms.assetid: b5cbc453-5986-423e-af44-1f243ef3edb1
caps.latest.revision: 43
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f2c66ebf45916b6e820a5599b4b90416703b377e
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="set-report-processing-properties"></a>レポート処理プロパティの設定
  レポート実行プロパティでは、レポートの処理方法を制御します。 実行プロパティは、各レポートごとに設定する必要があります。  
  
 レポート実行プロパティを設定するには、レポート マネージャーでレポートを開き、[実行] プロパティ ページに移動します。 詳細については、「[[処理オプション] プロパティ ページ &#40;レポート マネージャー&#41;](http://msdn.microsoft.com/library/28f07c70-7132-4d15-9505-4fdf31dc9cc0)」を参照してください。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用してプロパティを設定することもできます。「[[処理オプション] プロパティ ページ &#40;レポート マネージャー&#41;](http://msdn.microsoft.com/library/28f07c70-7132-4d15-9505-4fdf31dc9cc0)」を参照してください。  
  
## <a name="report-execution-modes"></a>レポート実行モード  
 レポートは、要求時に実行するか、スナップショットとして実行することができます。 以下のセクションでは、各方法について説明します。  
  
### <a name="running-reports-on-demand"></a>要求時にレポートを実行  
 ユーザーがレポートを実行するたびに、レポートがデータ ソースへのクエリを実行するように指定できます。これが、最新データが格納される要求時レポートになります。 レポートを開くユーザーまたはレポートを要求するユーザーごとに、レポートの新しいインスタンスが作成されます。それぞれの新しいインスタンスに、新しいクエリの結果が保持されます。 この方法を使用すると、10 人のユーザーが同時にレポートを開いた場合、10 のクエリがデータ ソースに送信され、処理されます。  
  
### <a name="running-reports-on-demand-from-cache"></a>要求時にキャッシュからレポートを実行  
 パフォーマンスを向上させるため、ユーザーがレポートを実行するときに、レポート (およびデータ) を一時的にキャッシュするよう指定できます。 キャッシュされたコピーは、それ以降に同じレポートにアクセスする他のユーザーも使用できます。 この方法では、10 人のユーザーがレポートを開いた場合、レポート処理が行われるのは、最初の要求に対してのみとなります。 続いてレポートがキャッシュされ、残りの 9 人のユーザーには、そのキャッシュされたレポートが表示されます。  
  
 キャッシュされたレポートは、定義された間隔でキャッシュから削除されます。 キャッシュを空にするは、分単位で間隔を指定したり、特定の日時にスケジュールすることができます。 詳細については、「[レポートのキャッシュ &#40;SSRS&#41;](../../reporting-services/report-server/caching-reports-ssrs.md)」を参照してください。  
  
### <a name="running-reports-from-snapshots"></a>スナップショットからレポートを実行  
 レポート スナップショットは、レイアウト情報および特定の時期に取得されるデータを含むレポートです。 レポートが予定外に (たとえば、スケジュールされたバックアップ中に) 実行されないように、レポートをレポート スナップショットとして実行することができます。 レポート スナップショットは、通常はスケジュールに従って作成され、その後更新されます。これによって、正確な時間でレポートとデータ処理を行うことができます。 レポートが実行に長時間かかるクエリに基づいている場合や、クエリに使用されているデータのデータ ソースが、ある一定時間の間アクセスを避けたいものである場合は、レポートをスナップショットとして実行してください。  
  
 レポート スナップショットは、レポート サーバー データベースに格納され、後でユーザーまたはプロセス (サブスクリプションなど) がレポートを要求したときに取得されます。 レポート スナップショットが更新されると、新しいインスタンスによって上書きされます。 レポート サーバーでは、レポート履歴に追加するように特別にオプションを設定しない限り、以前のバージョンのレポートを保存しません。 詳細については、「 [レポート履歴でのスナップショットの作成、変更、および削除](../../reporting-services/report-server/create-modify-and-delete-snapshots-in-report-history.md)」を参照してください。  
  
 すべてのレポートがスナップショットとして実行されるように構成できるとは限りません。 ユーザーに資格情報を要求するレポートや、Windows 統合セキュリティを使用してデータを取得するレポートのスナップショットを作成することはできません。 パラメーター化されたレポートをスナップショットとして実行する場合、スナップショットの作成時に使用する既定のパラメーターを指定する必要があります。 要求時に実行されるレポートとは異なり、レポートが開かれると、レポート スナップショットに対して別のパラメーター値を指定することはできません。 別のパラメーター値を選択すると、新しいレポート処理要求が生じますが、これは許可されません。  
  
 スナップショットとして実行するように要求時レポートを構成すると、場合によっては、サブスクリプションが非アクティブになることがあります。 次の条件で、レポート サーバーは、要求時にレポートを実行するように構成されていても、そのときに定義された既存のサブスクリプションを非アクティブにします。  
  
-   レポートがクエリ パラメーターを使用し、かつ、既定のパラメーターとして特定の値を選択し、レポートをスナップショットとして実行するための要件を満たすようにする場合。  
  
-   既存のサブスクリプションが、スナップショットに対して指定した既定のパラメーター値と異なるパラメーター値を使用するように構成されている場合。  
  
 この条件が存在する場合、レポート サーバーは、次にスケジュールされているサブスクリプションの実行時に、サブスクリプションを無効にします。 サブスクリプションを再度アクティブ化するには、サブスクリプションを開いてから保存します。 サブスクリプションを開くと、レポート サーバーにより、スナップショットに指定されたサブスクリプションのパラメーター値が更新されます。 サブスクリプションの詳細については「[サブスクリプションと配信 &#40;Reporting Services&#41](../../reporting-services/subscriptions/subscriptions-and-delivery-reporting-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [処理オプションの設定 &#40;Reporting Services の SharePoint 統合モード&#41;](../../reporting-services/report-server-sharepoint/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)   
 [レポートの実行プロパティを構成する &#40;レポート マネージャー&#41;](../../reporting-services/reports/configure-execution-properties-for-a-report-report-manager.md)   
 [Reporting Services の概念 &#40;SSRS&#41;](../../reporting-services/reporting-services-concepts-ssrs.md)   
 [レポート履歴にスナップショットを追加する方法](../../reporting-services/report-server/add-a-snapshot-to-report-history-report-manager.md)   
 [レポート データ ソースに関する資格情報と接続情報を指定する](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)  
  
  
