---
title: 共有データセットの [キャッシュ] ページ (レポートマネージャー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: eac372e9-d2a1-48a8-bbe5-09d101df16ea
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ae18d021465a7d14ea22b56534ea48ac316154c2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66109910"
---
# <a name="caching-page-shared-datasets-report-manager"></a>共有データセットの [キャッシュ] ページ (レポート マネージャー)
  共有データセットのキャッシュ オプションを設定するには、[キャッシュ] プロパティ ページを使用します。  
  
> [!NOTE]  
>  この機能は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。 の[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]各エディションでサポートされる機能の一覧については、「 [SQL Server 2014 の各エディションがサポートする機能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。  
  
## <a name="navigation"></a>「ナビゲーション」  
 このページに移動するには、次の手順に従います。  
  
### <a name="to-open-the-caching-properties-page-for-a-shared-dataset"></a>共有データセットの [キャッシュ] プロパティ ページを開くには  
  
1.  レポート マネージャーを開き、共有データセットのプロパティを構成するレポートを探します。  
  
2.  共有データセットの上にマウス ポインターを移動し、下矢印をクリックします。  
  
3.  ドロップダウン リストの **[管理]** をクリックします。 レポートの [全般] プロパティ ページが開きます。  
  
4.  **[キャッシュ]** タブをクリックします。  
  
## <a name="options"></a>オプション  
 **[共有データセットをキャッシュする]**  
 この共有データセットを使用するレポートをユーザーが最初に開いたときに、データの一時コピーをキャッシュに配置します。 キャッシュ期間内にレポートを実行する後続のユーザーは、データのキャッシュされたコピーを受け取ります。 再度データセット クエリを実行することなくデータがキャッシュから返されるので、通常はキャッシュによってパフォーマンスが向上します。  
  
 **[キャッシュが期限切れになるまでの時間 (分)]**  
 キャッシュされたデータのコピーを保存する時間 (分単位) を指定します。 一時コピーの有効期限が切れると、データはキャッシュから返されなくなります。 次にこの共有データセットを使用するレポートをユーザーが開いたときに、データセット クエリが実行され、レポート サーバーによって、更新されたデータのコピーがキャッシュに配置されます。  
  
 **[次のスケジュールでキャッシュを期限切れにします]**  
 キャッシュされたデータを無効にしてキャッシュから削除するタイミングを示すスケジュールを設定します。 このスケジュールは、共有スケジュールにすることも、現在の共有データセットのみに固有のスケジュールにすることもできます。  
  
 **[データセット固有のスケジュール]**  
 このデータセットのみによって使用されるスケジュールを指定します。  
  
 **共有スケジュール**  
 レポート、サブスクリプション、および他の共有データセットによって共有されるスケジュールを指定します。  
  
 適用****  
 変更を保存します。  
  
## <a name="see-also"></a>参照  
 [レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [レポートマネージャーの F1 ヘルプ](../../2014/reporting-services/report-manager-f1-help.md)   
 [SSRS&#41;&#40;共有データセットをキャッシュする](report-server/cache-shared-datasets-ssrs.md)   
 [スケジュール](subscriptions/schedules.md)  
  
  
