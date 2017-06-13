---
title: "Reporting Services サーバーのプロパティ ([セキュリティ] ページ) - |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.reportserver.serverproperties.security.f1
ms.assetid: f49aedc6-f145-4df1-8f69-d5d910f492c6
caps.latest.revision: 11
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8da36c90d2eb22600ad6560a37367e68de933971
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="server-properties-security-page---reporting-services"></a>[サーバーのプロパティ] ([セキュリティ] ページ) - Reporting Services
  [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] の [!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] ページを使用すると、レポート サーバーを危険にさらす可能性のある機能を無効にできます。 これらの機能を無効にすることで一部の機能が制限されますが、特定の脅威を緩和することで、レポート サーバー全体のセキュリティを向上させることができます。  
  
 このページを開くには:
 1) [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を起動します。
 2) レポート サーバー インスタンスに接続します。
 3) レポート サーバー名を右クリックして、 **[プロパティ]**をクリックします。 
 4) **[セキュリティ]** をクリックすると、このページが開きます。  
  
## <a name="options"></a>オプション  
 **[レポート データ ソースで Windows 統合セキュリティを有効にする]**  
 レポートを要求したユーザーの Windows セキュリティ トークンを使用してレポート データ ソースに接続するかどうかを指定します。  
  
 この機能を無効にすると、レポート データ ソースのプロパティ ページにある Windows 統合セキュリティ機能は使用できなくなります。 レポート データ ソースが Windows 統合セキュリティを使用するように構成されている場合、この機能を無効にすると、レポート サーバーによってすべてのデータ ソース接続プロパティが即時に更新され、資格情報が要求されるようになります。  
  
 **[カスタム レポートを有効にする]**  
 ユーザーがレポート ビルダーのレポートからアドホック クエリを実行できるようにするかどうかを指定します。実行できるようにした場合は、ユーザーが対象データをクリックすると新しいレポートが自動的に生成されます。  
  
 このオプションの設定によって、レポート サーバー上の **EnableLoadReportDefinition** プロパティの設定が **True** になるか **False**になるかが決まります。 このオプションをオフにするとプロパティが **False** に設定され、レポート サーバーはデータ探索中に作成されるクリックスルー レポートを生成しません。 **LoadReportDefinition** メソッドの呼び出しはすべてブロックされます。  
  
 この機能を無効にすることで、悪意のあるユーザーが **LoadReportDefinition** 要求でレポート サーバーを過負荷にするサービス拒否攻撃の脅威を緩和することができます。  
  
## <a name="see-also"></a>参照  
 [レポート サーバーのプロパティを設定する &#40;Management Studio&#41;](../../reporting-services/tools/set-report-server-properties-management-studio.md)   
 [Management Studio でレポート サーバーに接続する](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
 [レポート データ ソースに関する資格情報と接続情報を指定する](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Management Studio のレポート サーバーの F1 ヘルプ](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)  
  
  

