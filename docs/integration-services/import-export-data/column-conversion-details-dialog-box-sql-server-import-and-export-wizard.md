---
title: "[列変換の詳細] ダイアログ ボックス (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs"
ms.custom: 
ms.date: 02/16/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: import-export-data
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.dts.impexpwizard.issuedetails.f1
ms.assetid: e2d00a39-dfbd-4821-a4d8-a5bd1164ed4d
caps.latest.revision: "29"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 81ff6011b40700f75dba019356e3c0d80e94f969
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="column-conversion-details-dialog-box-sql-server-import-and-export-wizard"></a>[列変換の詳細] ダイアログ ボックス (SQL Server インポートおよびエクスポート ウィザード)
  **[データ型マッピングの確認]** ページで個別の列の行をダブルクリックすると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードの **[列変換の詳細]** ダイアログ ボックスが表示されます。 このページでは、個々の列の詳細な変換情報を確認できます。 この情報には次の項目が含まれます。
-   変換元と変換先の列のデータ型。
-   変換が必要な場合、ウィザードが実行するデータ型変換。
-   ウィザードが必要なデータ型変換を判断するために使用するデータ型マッピング ファイル。 

## <a name="screen-shot-of-the-column-conversion-details-page"></a>[列変換の詳細] ページのスクリーン ショット 
 次のスクリーンショットは、ユーザーが **[データ型マッピングの確認]** ページで行をダブルクリックした後の、ウィザードの **[列変換の詳細]** ダイアログ ボックスです。 **[データ型マッピングの確認]** ページについては、「 [[データ型マッピングの確認]](../../integration-services/import-export-data/review-data-type-mapping-sql-server-import-and-export-wizard.md)」をご覧ください。
 
この例には、次が示されています。
-   ソース SQL Server テーブルの `PersonID` 列は、`int` 型です。 ウィザードがこの型を SQL Server Integration Services (SSIS) の `DT_I4` データ型にマップします。これは、データ型マッピングファイルの MSSQLToSSIS10.xml を参照する、4 バイトの符号付き整数です。
-   変換先の SQL Server テーブルの `PersonID` 列も `int` 型です。 このウィザードにより同じ SSIS データ型にこの型がマップされます。
-   ウィザードが *[この列では変換は必要ありません]* で終了しています。
 
  
 ![インポートおよびエクスポート ウィザードの列変換ページ](../../integration-services/import-export-data/media/column-conversion.png "インポートおよびエクスポート ウィザードの列変換ページ") 
  
## <a name="whats-next"></a>次の操作  
 列変換の詳細を確認して **[OK]**をクリックすると、 **[列変換の詳細]** ダイアログ ボックスから **[データ型マッピングの確認]** ページに戻ります。 詳しくは、「 [[データ型マッピングの確認]](../../integration-services/import-export-data/review-data-type-mapping-sql-server-import-and-export-wizard.md)」をご覧ください。  

## <a name="see-also"></a>参照
[SQL Server インポートおよびエクスポート ウィザードのデータ型マッピング](../../integration-services/import-export-data/data-type-mapping-in-the-sql-server-import-and-export-wizard.md)
