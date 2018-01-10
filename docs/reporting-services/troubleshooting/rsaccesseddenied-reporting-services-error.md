---
title: "rsAccessedDenied - Reporting Services エラー | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: troubleshooting
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: rsAccessDenied error
ms.assetid: 2f76b1bf-96a2-4755-b76b-84e933220efc
caps.latest.revision: "21"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: b0963e7384b597c8e009375d28c87a8d66d8b99b
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="rsaccesseddenied---reporting-services-error"></a>rsAccessedDenied - Reporting Services エラー
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] エラー **rsAccessedDenied** は、操作を実行する権限がユーザーに与えられていない場合に発生します。 たとえば、レポートを開くためのロールが割り当てられていない場合や、必要な権限を使用してブラウザーを開かなかった場合などです。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード &#124; SharePoint モード|  
  
-   URL を指定してレポート サーバーへ直接アクセスしているときにこのエラーが発生した場合は、HTTP 401 エラーに例外がマップされます。  
  
-   レポート マネージャーやその他のツールを使用しているときに発生した場合は、エラー ページに表示されます。  
  
-   スケジュール設定された操作、サブスクリプション、または配信中に発生した場合は、レポート サーバーのログ ファイルにのみ記録されます。  
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|**製品名**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|**イベント ID**|rsAccessedDenied|  
|**イベント ソース**|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|**コンポーネント**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|**メッセージ テキスト**|ユーザー 'mydomain\myAccount' には、この操作を行うのに必要な権限が与えられていません。 (rsAccessDenied) (ReportingServicesLibrary)。|  
  
## <a name="user-action"></a>ユーザーの操作  
 レポート サーバーのコンテンツや操作にアクセスする権限は、ロールの割り当てによって与えられます。 新規インストールを実行した時点では、ローカル管理者のみがレポート サーバーにアクセスできます。 他のユーザーがレポート サーバーにアクセスできるようにするには、ローカル管理者が、ドメインのユーザー アカウントやグループ アカウントを指定するロールの割り当て、ユーザーが実行できるタスクを定義する 1 つ以上のロール、およびスコープ (通常は、レポート サーバー フォルダー階層のルート ノードである [ホーム] フォルダー) を作成する必要があります。 レポート マネージャーを使用すると、ロールの割り当てを作成できます。 詳細については、SQL Server オンライン ブックの「ロールの割り当て」を参照してください。  
  
 このエラーは、レポート サーバーのローカル管理が原因で発生することもあります。 詳細については、「 [ローカル管理用のネイティブ モードのレポート サーバー &#40;SSRS&#41; の構成](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ロールの割り当て](../../reporting-services/security/role-assignments.md)   
 [ネイティブ モードのレポート サーバーに対する権限の許可](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)   
 [ロールと権限 &#40;Reporting Services&#41;](../../reporting-services/security/roles-and-permissions-reporting-services.md)  
  
  
