---
title: '[オプション] ([データセットのプロパティ] ダイアログボックス)Microsoft Docs'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10130"
- sql12.rtp.rptdesigner.datasetproperties.options.f1
ms.assetid: 95299049-71ba-427f-b723-775cb696243f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 778365e8fc7f40700b0f8c1683260f15c860a32a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66109410"
---
# <a name="dataset-properties-dialog-box-options"></a>[オプション] ([データセットのプロパティ] ダイアログ ボックス)
  [ **Datasetproperties** ] ダイアログボックスの [**オプション**] を選択すると、クエリの照合順序オプションや小計などのデータオプションを変更できます。 詳細については、「 [Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **Collation**  
 データの並べ替えに使用される照合順序を決めるロケールを選択します。 **[既定]** は、レポート サーバーが、レポートの実行時にデータ プロバイダーから値の取得を試みる必要があることを示します。 値を取得できない場合、既定値はコンピューターのロケール設定から取得されます。  
  
 **大文字と小文字の区別**  
 大文字と小文字の区別を決める値を選択します。 データが大文字と小文字を区別するかどうかを示します。 **大文字と小文字の区別**は、 **True**、 **False**、または**Auto**に設定できます。既定値の [**自動**] は、レポートサーバーがレポートの実行時にデータプロバイダーから値の取得を試みる必要があることを示します。 データ プロバイダーが大文字と小文字の区別をサポートしない場合、レポートは値が **[False]** の場合と同じように実行されます。 値を正確に把握しており、その値が確実にサポートされる場合は、 **[True]** を選択します。  
  
 **[アクセントの区別]**  
 アクセントの区別を決める値を選択します。 **アクセントの区別**は、データがアクセントを区別するかどうかを示し、 **True**、 **False**、または**Auto**に設定できます。既定値の [**自動**] は、レポートサーバーがレポートの実行時にデータプロバイダーから値の取得を試みる必要があることを示します。 データ プロバイダーがアクセントの区別をサポートしない場合、レポートは値が **[False]** の場合と同じように実行されます。 値を正確に把握しており、その値が確実にサポートされる場合は、 **[True]** を選択します。  
  
 **[かなの区別]**  
 かなの区別を決める値を選択します。 このオプションは、データがかな区別機微であるかどうかを示します。この値は、 **True**、 **False**、または**Auto**に設定できます。既定値の [**自動**] は、レポートサーバーがレポートの実行時にデータプロバイダーから値の取得を試みる必要があることを示します。 データ プロバイダーがかなの区別をサポートしない場合、レポートは値が **[False]** の場合と同じように実行されます。 値を正確に把握しており、その値が確実にサポートされる場合は、 **[True]** を選択します。  
  
 **[文字幅の区別]**  
 文字幅の区別を決める値を選択します。 このオプションは、データが文字幅を区別し、 **True**、 **False**、または**Auto**に設定できるかどうかを示します。既定値の [**自動**] は、レポートサーバーがレポートの実行時にデータプロバイダーから値の取得を試みる必要があることを示します。 データ プロバイダーが文字幅の区別をサポートしない場合、レポートは値が **[False]** の場合と同じように実行されます。 値を正確に把握しており、その値が確実にサポートされる場合は、 **[True]** を選択します。  
  
 **[小計を詳細行として解釈]**  
 集計行ではなく詳細行として小計行を解釈するかどうかを示す値を選択します。 既定値の [**自動**] は、レポートでデータセット内のフィールドにアクセスするために`Aggregate`() 関数が使用されていない場合に、小計行を詳細行として処理することを示します。 小計行を集計行として解釈する必要がある場合は、 **[False]** を選択します。 小計行を詳細行として解釈し、その行が`Aggregate`() 関数を使用しないことがわかっている場合は、[ **True**] を選択します。  
  
## <a name="see-also"></a>参照  
 [レポートまたはテキストボックスのロケールを &#40;Reporting Services に設定&#41;](report-design/set-the-locale-for-a-report-or-text-box-reporting-services.md)   
 [レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する](report-data/report-datasets-ssrs.md)   
 [Windows 照合順序名 &#40;Transact-SQL&#41;](/sql/t-sql/statements/windows-collation-name-transact-sql)   
 [SQL Server 照合順序名 &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql)   
 [集計関数 (レポート ビルダーおよび SSRS)](report-design/report-builder-functions-aggregate-function.md)  
  
  
