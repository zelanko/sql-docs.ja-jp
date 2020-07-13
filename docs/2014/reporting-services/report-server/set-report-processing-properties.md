---
title: レポート処理プロパティの設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- on-demand reports
- report processing [Reporting Services], execution properties
- snapshots [Reporting Services], running reports from
- cached reports [Reporting Services]
- report snapshots [Reporting Services], running reports from
- report execution snapshots [Reporting Services]
ms.assetid: b5cbc453-5986-423e-af44-1f243ef3edb1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a793fa513ef13c9cafc210a411971a0363f5976d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66103238"
---
# <a name="set-report-processing-properties"></a>レポート処理プロパティの設定
  レポート実行プロパティでは、レポートの処理方法を制御します。 実行プロパティは、各レポートごとに設定する必要があります。  
  
 レポート実行プロパティを設定するには、レポート マネージャーでレポートを開き、[実行] プロパティ ページに移動します。 また、を使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]プロパティを設定することもできます。 詳細については、「[[処理オプション] プロパティ ページ &#40;レポート マネージャー&#41;](../processing-options-properties-page-report-manager.md)」を参照してください。  
  
## <a name="report-execution-modes"></a>レポート実行モード  
 レポートは、要求時に実行するか、スナップショットとして実行することができます。 以下のセクションでは、各方法について説明します。  
  
### <a name="running-reports-on-demand"></a>要求時にレポートを実行  
 ユーザーがレポートを実行するたびに、レポートがデータ ソースへのクエリを実行するように指定できます。これが、最新データが格納される要求時レポートになります。 レポートを開くユーザーまたはレポートを要求するユーザーごとに、レポートの新しいインスタンスが作成されます。それぞれの新しいインスタンスに、新しいクエリの結果が保持されます。 この方法を使用すると、10 人のユーザーが同時にレポートを開いた場合、10 のクエリがデータ ソースに送信され、処理されます。  
  
### <a name="running-reports-on-demand-from-cache"></a>要求時にキャッシュからレポートを実行  
 パフォーマンスを向上させるため、ユーザーがレポートを実行するときに、レポート (およびデータ) を一時的にキャッシュするよう指定できます。 キャッシュされたコピーは、それ以降に同じレポートにアクセスする他のユーザーも使用できます。 この方法では、10 人のユーザーがレポートを開いた場合、レポート処理が行われるのは、最初の要求に対してのみとなります。 続いてレポートがキャッシュされ、残りの 9 人のユーザーには、そのキャッシュされたレポートが表示されます。  
  
 キャッシュされたレポートは、定義された間隔でキャッシュから削除されます。 キャッシュを空にするは、分単位で間隔を指定したり、特定の日時にスケジュールすることができます。 詳細については、「 [レポートのキャッシュ (SSRS)](caching-reports-ssrs.md)でキャッシュを事前に読み込む唯一の方法でした。  
  
### <a name="running-reports-from-snapshots"></a>スナップショットからレポートを実行  
 レポート スナップショットは、レイアウト情報および特定の時期に取得されるデータを含むレポートです。 レポートが予定外に (たとえば、スケジュールされたバックアップ中に) 実行されないように、レポートをレポート スナップショットとして実行することができます。 レポート スナップショットは、通常はスケジュールに従って作成され、その後更新されます。これによって、正確な時間でレポートとデータ処理を行うことができます。 レポートが実行に長時間かかるクエリに基づいている場合や、クエリに使用されているデータのデータ ソースが、ある一定時間の間アクセスを避けたいものである場合は、レポートをスナップショットとして実行してください。  
  
 レポート スナップショットは、レポート サーバー データベースに格納され、後でユーザーまたはプロセス (サブスクリプションなど) がレポートを要求したときに取得されます。 レポート スナップショットが更新されると、新しいインスタンスによって上書きされます。 レポート サーバーでは、レポート履歴に追加するように特別にオプションを設定しない限り、以前のバージョンのレポートを保存しません。 詳細については、「 [レポート履歴でのスナップショットの作成、変更、および削除](create-modify-and-delete-snapshots-in-report-history.md)」を参照してください。  
  
 すべてのレポートがスナップショットとして実行されるように構成できるとは限りません。 ユーザーに資格情報を要求するレポートや、Windows 統合セキュリティを使用してデータを取得するレポートのスナップショットを作成することはできません。 パラメーター化されたレポートをスナップショットとして実行する場合、スナップショットの作成時に使用する既定のパラメーターを指定する必要があります。 要求時に実行されるレポートとは異なり、レポートが開かれると、レポート スナップショットに対して別のパラメーター値を指定することはできません。 別のパラメーター値を選択すると、新しいレポート処理要求が生じますが、これは許可されません。  
  
 スナップショットとして実行するように要求時レポートを構成すると、場合によっては、サブスクリプションが非アクティブになることがあります。 次の条件で、レポート サーバーは、要求時にレポートを実行するように構成されていても、そのときに定義された既存のサブスクリプションを非アクティブにします。  
  
-   レポートがクエリ パラメーターを使用し、かつ、既定のパラメーターとして特定の値を選択し、レポートをスナップショットとして実行するための要件を満たすようにする場合。  
  
-   既存のサブスクリプションが、スナップショットに対して指定した既定のパラメーター値と異なるパラメーター値を使用するように構成されている場合。  
  
 この条件が存在する場合、レポート サーバーは、次にスケジュールされているサブスクリプションの実行時に、サブスクリプションを無効にします。 サブスクリプションを再度アクティブ化するには、サブスクリプションを開いてから保存します。 サブスクリプションを開くと、レポート サーバーにより、スナップショットに指定されたサブスクリプションのパラメーター値が更新されます。 サブスクリプションの詳細については、「[サブスクリプションと配信 &#40;Reporting Services&#41](../subscriptions/subscriptions-and-delivery-reporting-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SharePoint 統合モードで Reporting Services &#40;処理オプションを設定&#41;](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)   
 [レポート &#40;レポートマネージャーの実行プロパティの構成&#41;](../reports/configure-execution-properties-for-a-report-report-manager.md)   
 [SSRS&#41;&#40;の Reporting Services の概念](../reporting-services-concepts-ssrs.md)   
 [レポート履歴にスナップショットを追加する方法](add-a-snapshot-to-report-history-report-manager.md)   
 [レポート データ ソースに関する資格情報と接続情報を指定する](../report-data/specify-credential-and-connection-information-for-report-data-sources.md)  
  
  
