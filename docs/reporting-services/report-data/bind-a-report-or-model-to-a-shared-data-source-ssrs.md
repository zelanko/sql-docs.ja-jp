---
title: レポートまたはモデルを共有データ ソースにバインドする (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-data
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- shared data sources [Reporting Services]
- data sources [Reporting Services], shared
ms.assetid: 23cc15f2-2883-48e2-bc6c-fa0ab61a2e21
caps.latest.revision: 11
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 708cfa2d2a587ab9990f1b5a1c4a28691229fa88
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="bind-a-report-or-model-to-a-shared-data-source-ssrs"></a>レポートまたはモデルを共有データ ソースにバインドする (SSRS)
  レポートまたはモデルをテスト サーバーから実稼働サーバーに移動するときなど、ファイルをローカル コンピューターに保存した後で別のレポート サーバーにアップロードする操作が必要になる場合があります。 レポートまたはモデルを新しいサーバーにアップロードしたときは、新しいレポート サーバー上に格納されている共有データ ソースにレポートまたはモデルを再バインドする必要があります。 レポートまたはモデルの再バインドを行わないと、レポートまたはモデルが新しいレポート サーバーからアクセスされたときに正常に動作しない場合があります。  
  
> [!IMPORTANT]  
>  レポートまたはモデルを共有データ ソースに再バインドする前に、データ ソースがレポート サーバーまたは SharePoint ライブラリに存在している必要があります。 データ ソースの詳細については、「[共有データ ソースを作成、変更、および削除する (SSRS)](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md)」を参照してください。  
  
### <a name="to-bind-a-report-or-model-to-a-shared-data-source-on-a-report-server-running-in-native-mode"></a>ネイティブ モードで実行されているレポート サーバー上の共有データ ソースにレポートまたはモデルをバインドするには  
  
1.  **レポート マネージャー**で、サーバーにアップロードしたレポートまたはモデルの名前をクリックします。  
  
     [プロパティ] タブが開きます。  
  
2.  **[データ ソース]** をクリックします。  
  
3.  **[参照]** をクリックし、レポートまたはモデルをバインドするデータ ソースを参照します。  
  
4.  データ ソースを選択し、 **[OK]** をクリックします。  
  
5.  **[適用]** をクリックします。  
  
     選択したデータ ソースにレポートまたはモデルがバインドされます。  
  
### <a name="to-bind-a-report-or-model-to-a-shared-data-source-on-a-report-server-running-in-sharepoint-integrated-mode"></a>SharePoint 統合モードで実行されているレポート サーバー上の共有データ ソースにレポートまたはモデルをバインドするには  
  
1.  まだライブラリが開いていない場合は、クイック起動バーでライブラリの名前をクリックします。 ライブラリの名前が表示されていない場合は、 **[すべてのサイト コンテンツの表示]** をクリックし、ライブラリの名前をクリックします。  
  
2.  レポートまたはモデルをポイントし、下矢印をクリックします。  
  
3.  **[データ ソースの管理]** をクリックします。  
  
4.  **[dataSource1]** をクリックします。  
  
5.  **[接続の種類]** 領域で、 **[共有データ ソース]** が選択されていることを確認します。  
  
6.  **[データ ソース リンク]** 領域で、省略記号ボタン ([...]) をクリックします。  
  
7.  使用するデータ ソースを探します。  
  
8.  データ ソースを選択し、 **[OK]** をクリックします。  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
10. **[閉じる]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [ファイルまたはレポートをアップロードする (レポート マネージャー)](../../reporting-services/reports/upload-a-file-or-report-report-manager.md)   
 [SharePoint ライブラリへのドキュメントのアップロード (Reporting Services の SharePoint モード)](../../reporting-services/report-server-sharepoint/upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md)   
 [共有データ ソースを作成および管理する (Reporting Services の SharePoint 統合モード)](http://msdn.microsoft.com/library/2d3428e4-a810-4e66-a287-ff18e57fad76)   
 [共有データ ソースを作成、削除、または変更する (レポート マネージャー)](http://msdn.microsoft.com/library/cd7bace3-f8ec-4ee3-8a9f-2f217cdca9f2)   
 [データ接続、データ ソース、および接続文字列 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)   
 [Reporting Services でサポートされるデータ ソース &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md)  
  
  
