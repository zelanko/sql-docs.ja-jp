---
title: "外部アイテム (レポート ビルダーおよび SSRS) へのパスを指定する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4fe513da-f3c5-479c-9fec-8662b91a0d6d
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3ba2c751b7f851fa9be24ca08cb4ab95f4314258
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="specifying-paths-to-external-items-report-builder-and-ssrs"></a>外部アイテムへのパスの指定 (レポート ビルダーおよび SSRS)
  詳細レポート、サブレポート、画像ファイルなど、レポート定義ファイルの外部にあり、レポート サーバーに保存されるアイテムを参照するには、レポート アイテム プロパティに目的のアイテムへのパスを指定します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
> [!NOTE]  
>  レポート ビルダーでは、レポート サーバー上のアイテムへのパスを指定する必要があります。 ファイル システム上のアイテムへのパスはサポートされません。 これらのアイテムを使用するレポートは、アイテムが格納されているレポート サーバーに接続している場合にのみプレビューできます。  
  
 アクション、サブレポート、または画像のダイアログ ボックスで外部アイテムへのパスを指定する場合は、レポート サーバーを直接参照してアイテムを選択することができます。 詳細レポートまたはサブレポートを指定する場合は、アイテムを直接参照して選択することをお勧めします。 そうすると、レポートまたはサブレポートのパラメーターを指定するときに、ドロップダウン リストから適切なパラメーター名を選択できるようになります。 別のアイテムを指すようにアイテム パスを変更する場合は、必要に応じてパラメーターの名前と値を適切なものに手動で更新する必要があります。  
  
 ネイティブ モードで構成されているレポート サーバーでは、ファイル拡張子 .rdl を含まない詳細レポート名を指定します。  
  
 SharePoint 統合モードで構成されているレポート サーバーでは、ファイル拡張子 .rdl を含める必要があります。 次のいずれかのパスを指定できます。  
  
-   **メイン レポートからアイテムへの相対パス。** たとえば、../AllSubreports/Subreport1 のように指定します。 この例で、 **..** は、メイン レポートが格納されているフォルダーの 1 つ上のフォルダーを示します。  
  
    > [!NOTE]  
    >  レポート ビルダーの内部でレポートを実行する場合、相対パスはサポートされません。 外部アイテムへの相対パスを使用するレポートを表示するには、レポート サーバーにレポートを保存し、そこからレポートを実行します。  
  
-   **アイテムへの完全パス。**  
  
    -   **レポート サーバーの場合** 、完全パスはホーム フォルダーである **/**から開始します。 たとえば、/Reports/AllSubreports/Subreport1 のように指定します。  
  
    -   **SharePoint サイトの場合** 、アイテムの完全な URL とファイル拡張子 .rdl を含めたレポート名を式で指定する必要があります。 たとえば、 `="http://server/site/library/folder/Report1.rdl"`のようにします。  
  
## <a name="see-also"></a>参照  
 [外部の画像の追加 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/add-an-external-image-report-builder-and-ssrs.md)   
 [サブレポートおよびパラメーターの追加 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/add-a-subreport-and-parameters-report-builder-and-ssrs.md)   
 [レポートへのドリルスルー アクションの追加 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/add-a-drillthrough-action-on-a-report-report-builder-and-ssrs.md)  
  
  
