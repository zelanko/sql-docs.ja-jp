---
title: '[サーバーのプロパティ] ([セキュリティ] ページ) - Reporting Services | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.security.f1
ms.assetid: f49aedc6-f145-4df1-8f69-d5d910f492c6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 9513e66b92a97f1d546d7b33cc20849e8bff868a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48161442"
---
# <a name="server-properties-security-page---reporting-services"></a>[サーバーのプロパティ]\([セキュリティ] ページ) - Reporting Services
  このページを使用すると、レポート サーバーを危険にさらす可能性のある機能を無効にできます。 これらの機能を無効にすることで一部の機能が制限されますが、特定の脅威を緩和することで、レポート サーバー全体のセキュリティを向上させることができます。  
  
 このページを開くには、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を起動してレポート サーバー インスタンスに接続し、レポート サーバー名を右クリックして **[プロパティ]** をクリックします。 **[セキュリティ]** をクリックすると、このページが開きます。  
  
## <a name="options"></a>および  
 **[レポート データ ソースで Windows 統合セキュリティを有効にする]**  
 レポートを要求したユーザーの Windows セキュリティ トークンを使用してレポート データ ソースに接続するかどうかを指定します。  
  
 この機能を無効にすると、レポート データ ソースのプロパティ ページにある Windows 統合セキュリティ機能は使用できなくなります。 レポート データ ソースが Windows 統合セキュリティを使用するように構成されている場合、この機能を無効にすると、レポート サーバーによってすべてのデータ ソース接続プロパティが即時に更新され、資格情報が要求されるようになります。  
  
 **[カスタム レポートを有効にする]**  
 ユーザーがレポート ビルダーのレポートからアドホック クエリを実行できるようにするかどうかを指定します。実行できるようにした場合は、ユーザーが対象データをクリックすると新しいレポートが自動的に生成されます。  
  
 このオプションの設定によって、レポート サーバー上の `EnableLoadReportDefinition` プロパティの設定が `True` になるか `False` になるかが決まります。 このオプションをオフにした場合、プロパティに設定されます`False`とレポート サーバーはデータの探索中に作成されるクリックスルー レポートを生成しません。 `LoadReportDefinition` メソッドの呼び出しはすべてブロックされます。  
  
 悪意のあるユーザーがレポート サーバーを過、サービス拒否攻撃を起動するため、脅威を緩和するこのオプションをオフにする`LoadReportDefinition`要求。  
  
## <a name="see-also"></a>参照  
 [レポート サーバーのプロパティを設定する (Management Studio)](set-report-server-properties-management-studio.md)   
 [Management Studio でレポート サーバーに接続する](connect-to-a-report-server-in-management-studio.md)   
 [資格情報とレポート データ ソースの接続情報を指定する](../report-data/specify-credential-and-connection-information-for-report-data-sources.md[のレポート サーバーの Management Studio の F1 ヘルプ](report-server-in-management-studio-f1-help.md)  
  
  
