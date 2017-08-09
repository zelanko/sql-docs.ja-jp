---
title: "(レポート ビルダーおよび SSRS) レポートからデータ フィードの生成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e68baae2-9f2a-4f13-9179-9ac7f29111c5
caps.latest.revision: 11
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: b49b80de8516e14972b05d7ae91f4f72e765803a
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---

# <a name="generate-data-feeds-from-a-report-report-builder-and-ssrs"></a>1 つのレポートからのデータ フィードの生成 (レポート ビルダーおよび SSRS)

改ページ調整されたレポートから Atom 準拠のデータ フィードを生成して Power Pivot など、アプリケーションでデータ フィードを使用またはフィードの Power BI でデータを利用することができます。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Atom 表示拡張機能では、レポートで使用可能なデータ フィードを一覧表示する Atom サービス ドキュメントが生成されます。 このドキュメントには、レポート内の各データ領域について 1 つ以上のデータ フィードが一覧表示されます。 データ領域の種類およびデータ領域に表示されるデータによっては、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] は、1 つのデータ領域から複数のデータ フィードを生成することがあります。  
  
 Atom サービス ドキュメントには、データ フィードごとに一意の識別子が含まれています。データ フィードの内容を表示するには、URL でこの識別子を使用します。  
  
 詳しくは、「[複数のレポートからのデータ フィードの生成 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md)」をご覧ください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-generate-an-atom-service-document"></a>Atom サービス ドキュメントを生成するには  
  
1.  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Web ポータルで、データ フィードを生成するレポートに移動します。  
  
2.  レポートをクリックします。  
  
     レポートが実行されます。  
  
3.  ツール バーで、 **[データ フィードへエクスポート]** アイコンをクリックします。  
  
     データ フィードを含む Atom ドキュメントを保存するか開くかを確認するメッセージが表示されます。  
  
4.  **[保存]** をクリックしてドキュメントをファイル システムに保存するか、 **[開く]** をクリックして保存の前にドキュメントの内容を表示します。 **既定では、ブラウザーにドキュメントが開きます。**  
  
5.  ドキュメントを保存する場所を参照します。  
  
6.  必要に応じてドキュメントの名前を変更できます。  
  
    > [!NOTE]  
    >  既定では、ドキュメント名がレポート名になります。  
  
7.  ドキュメントの種類が、 **ATOMSVC ファイル**であることを確認し、 **[保存]**をクリックします。  
  
8.  必要に応じて、ブラウザーで、またはテキスト エディターか XML エディターで、.atomsvc ファイルを開きます。  
  
### <a name="to-view-an-atom-compliant-data-feed"></a>Atom 準拠のデータ フィードを表示するには  
  
1.  Atom サービス ドキュメントがまだ開かれていない場合は、そのサービス ドキュメントを検索し、Internet Explorer などのブラウザーで開きます。  
  
2.  表示するデータ フィードの URL を Atom サービス ドキュメントからブラウザーにコピーします。  
  
     URL の形式は次のとおりです。  
  
     `http://<server name>/ReportServer?%2f<ReportName>rs%3aCommand=Render&rs%3aFormat=ATOM&rc%3aDataFeed=<Identifier>`  
  
3.  Enter キーを押します。  
  
     データ フィードを含む Atom ドキュメントを保存するか開くかを確認するメッセージが表示されます。  
  
4.  **[保存]** をクリックしてドキュメントをファイル システムに保存するか、 **[開く]** をクリックして保存の前にデータ フィードを表示します。  
  
5.  ドキュメントを保存する場所を参照します。  
  
6.  必要に応じてドキュメントの名前を変更できます。  
  
    > [!NOTE]  
    >  既定では、ドキュメント名がレポート名になります。 Atom サービス ドキュメントに複数のフィードがある場合、既定ではすべて同じ名前 (レポート名) が使用されます。 それらを区別するには、名前を変更してわかりやすい名前を使用してください。  
  
7.  ドキュメントの種類が、 **ATOM ファイル**であることを確認し、 **[保存]**をクリックします。  
  
8.  必要に応じて、ブラウザーで、またはテキスト エディターか XML エディターで、.atom ファイルを開きます。  

## <a name="next-steps"></a>次の手順

[レポートのエクスポート](../../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md)  

他に質問しますか。 [Reporting Services のフォーラムで質問してみてください。](http://go.microsoft.com/fwlink/?LinkId=620231)
