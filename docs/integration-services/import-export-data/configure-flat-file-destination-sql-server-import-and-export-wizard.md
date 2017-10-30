---
title: "フラット ファイル変換先 (SQL Server インポートおよびエクスポート ウィザード) を構成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.configureflatfiledest.f1
ms.assetid: 318e8da0-37d3-46cd-943a-fc5d66aad93a
caps.latest.revision: 53
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 560965a241b24a09f50a23faf63ce74d0049d5a7
ms.openlocfilehash: 93fbd5e9429d06e3f011f6f0aff03d76a3db9000
ms.contentlocale: ja-jp
ms.lasthandoff: 10/13/2017

---
# <a name="configure-flat-file-destination-sql-server-import-and-export-wizard"></a>[フラット ファイルの変換先の構成] \(SQL Server インポートおよびエクスポート ウィザード)
  フラット ファイル変換先を選択した場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インポートおよびエクスポート ウィザードの番組**フラット ファイル変換先の構成**テーブルをコピーすることを指定するクエリを指定する後またはします。 このページで、宛先のフラット ファイルの書式設定オプションを指定します 必要に応じて、個々の列のマッピングを確認し、サンプル データをプレビューします。  
  
## <a name="screen-shot-of-the-configure-flat-file-destination-page"></a>[フラット ファイル変換先の構成] ページのスクリーン ショット  
 スクリーン ショットを次の例を示しています、**フラット ファイル変換先の構成**ウィザードのページです。
 
 この例では、ユーザーが一般的な CSV (コンマ区切り) ファイルを作成するのには、次のオプションを指定します。
-   **行区切り記号**」を参照してください。 出力内のデータの各行は、キャリッジ リターン、ライン フィードの組み合わせで終了します。
-   **列区切り記号**」を参照してください。 列の各行に含まれるデータは、コンマで区切られます。

 ![インポートおよびエクスポート ウィザードのフラット ファイル ページを構成します。](../../integration-services/import-export-data/media/flat-file.png)
  
## <a name="pick-a-source-table"></a>ソース テーブルを選択します。
 **ソース テーブルまたはビュー**  
-   指定した場合、前のページでテーブルをコピーすること、ドロップダウン リストから、ソース テーブルまたはビューを選択します。
-   場合は、クエリを指定した`"Query"`が選択され、唯一のオプションがします。  

## <a name="specify-row-and-column-delimiters-for-the-output"></a>出力の行と列の区切り記号を指定します。
 **[行区切り記号]**  
 出力に行を区切る区切り記号の一覧から選択します。 指定するオプションはありません、*カスタム*行区切り記号。  
  
|値|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|復帰と改行の組み合わせで行を区切ります。|  
|**{CR}**|復帰で行を区切ります。|  
|**{LF}**|改行で行を区切ります。|  
|**セミコロン {;}**|セミコロンで行を区切ります。|  
|**コロン {:}**|コロンで行を区切ります。|  
|**コンマ {,}**|コンマで行を区切ります。|  
|**タブ {t}**|タブで行を区切ります。|  
|**縦棒 {&#124;}**|垂直バーで行を区切ります。|  
  
 **列区切り記号**  
 出力に列を区切る区切り記号の一覧から選択します。 指定するオプションはありません、*カスタム*列区切り記号。  
  
|値|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|復帰と改行の組み合わせで列を区切ります。|  
|**{CR}**|復帰で列を区切ります。|  
|**{LF}**|改行で列を区切ります。|  
|**セミコロン {;}**|セミコロンで列を区切ります。|  
|**コロン {:}**|コロンで列を区切ります。|  
|**コンマ {,}**|コンマで列を区切ります。|  
|**タブ {t}**|タブで列を区切ります。|  
|**縦棒 {&#124;}**|垂直バーで列を区切ります。|  

## <a name="optionally-review-column-mappings-and-preview-data"></a>必要に応じて、列マッピングを確認し、データをプレビュー

**マッピングの編集**   
必要に応じて、をクリックして**マッピングを編集する**を表示する、**列マッピング**選択したテーブルのダイアログ ボックス。 **[列マッピング]** ダイアログ ボックスを使用して、次のことを行います。
-   変換元と変換先の間の個々の列のマッピングを確認します。
-   列のサブセットのみをコピーするには、コピーしない列について **[無視]** を選択します。

詳細については、「 [列マッピング](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md)」を参照してください。  

**プレビュー**  
必要に応じて、をクリックして**プレビュー**サンプル内のデータを最大 200 行をプレビューする、**データのプレビュー**  ダイアログ ボックス。 プレビューで、コピーしたいデータがウィザードによってコピーされることを確認します。 詳細については、 [データのプレビュー](../../integration-services/import-export-data/preview-data-dialog-box-sql-server-import-and-export-wizard.md)に関するページを参照してください。  
  
データをプレビューした後で、ウィザードの前のページで選択したオプションを変更してもかまいません。 これらの変更を行うには、 **[フラット ファイルの変換先の構成]** ページに戻り、 **[戻る]** をクリックし、選択の変更が可能な前のページに戻ります。  

## <a name="whats-next"></a>次の操作  
 変換先のフラット ファイルの書式設定オプションを指定すると、次のページは **[パッケージの保存および実行]**となります。 このページでは、操作をすぐに実行するかどうかを指定します。 構成によっては、またことができますと設定を保存する、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]パッケージをカスタマイズして、後で再利用します。 詳細については、 [パッケージの保存および実行](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md)に関するページを参照してください。  


