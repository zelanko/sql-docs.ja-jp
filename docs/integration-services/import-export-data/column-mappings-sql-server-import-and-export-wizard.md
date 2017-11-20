---
title: "列のマッピング (SQL Server インポートおよびエクスポート ウィザード) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: import-export-data
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.columnmapandtransform.f1
ms.assetid: eadc54a6-f936-4ffc-91d7-fbfd2bdcab93
caps.latest.revision: 69
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b1ed879f21396c3c8d588307eaf087daea8c44c3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="column-mappings-sql-server-import-and-export-wizard"></a>[列マッピング]\(SQL Server インポートおよびエクスポート ウィザード)
  指定したクエリをコピーまたは確認する既存のテーブルやビューを選択した後、 **[マッピングの編集]**をクリックすると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインポートおよびエクスポート ウィザードに **[列マッピング]** ダイアログ ボックスが表示されます。 このページを指定し、ソース列からコピーしたデータを受信する変換先列を構成します。 多くの場合、このページで何も変更する必要はありません。
  
選択したテーブル内のすべての列をコピーしない場合は、このページで行うことができますしている必要がない列を除外します。 選択**無視**で、**先**の列、**マッピング**をコピーする列の一覧です。
 
## <a name="screen-shot-of-the-column-mappings-page"></a>[列マッピング] ページのスクリーン ショット 
 スクリーン ショットを次の例を示しています、**列マッピング**ウィザードのダイアログ ボックス。 
 
 この例では、 **[変換先テーブルを作成する]** が選択されているので、ウィザードで新しい変換先テーブルを作成しようとしているのがわかります。 既定では、ウィザードは、対応するソース列と各新しいレプリケーション先テーブルの同じ名前の列、データ型、およびプロパティを示します。 
  
 ![インポートおよびエクスポート ウィザードの [列マッピング] ページ](../../integration-services/import-export-data/media/column-mappings.png "インポートおよびエクスポート ウィザードの [列マッピング] ページ")  
  
## <a name="review-the-source-and-destination"></a>ソースと宛先を確認します。 
![列マッピング ページ、ソースおよび変換先のセクション](../../integration-services/import-export-data/media/column-mappings-page-source-and-destination-section.png)

 **ソース**  
 選択したソース テーブル、ビュー、またはクエリ。  
  
 **変換先**  
 選択した対象テーブルまたはビュー。  

## <a name="optionally-create-a-new-destination-table"></a>必要に応じて、新しいレプリケーション先テーブルを作成します。
![列マッピング ページのテーブルの新しいセクション](../../integration-services/import-export-data/media/column-mappings-page-new-table-section.png)

 **変換先テーブル/ファイルの作成**  
 既に存在しない場合は、コピー先のテーブルを作成します。    
  
 **SQL の編集**  
**[SQL の編集]** をクリックすると、 **[テーブル作成 SQL ステートメント]** ダイアログ ボックスが開きます。 自動生成された CREATE TABLE ステートメントを使用してまたは用途に合わせて変更します。 このステートメントを手動で変更する場合は、変更内容が列マッピングの一覧に反映されていることを確認する必要があります。 詳細については、「 [[テーブル作成 SQL ステートメント] (SQL Server インポートおよびエクスポート ウィザード)](../../integration-services/import-export-data/create-table-sql-statement-sql-server-import-and-export-wizard.md)」を参照してください。  

### <a name="sometimes-these-options-are-disabled"></a>これらのオプションが無効になっている場合があります。
**変換先テーブルのファイルを作成する**オプションおよび**SQL の編集**ボタンは自動的に有効になっているか自動的に無効にします。

-   **有効になります。** 指定した場合、**新しい**上の宛先テーブル、 **ソース テーブルおよびビュー**  ページで、**変換先テーブルを作成する**オプションが自動的に選択し、 **SQL の編集**ボタンが有効にします。

-   **無効になります。** 選択した場合、**既存**上の宛先テーブル、 **[ソース テーブルおよびビュー** ] ページで、**変換先テーブルを作成する**オプションおよび**SQL の編集**ボタンが無効になります。 新しいレプリケーション先テーブルを作成する場合に戻って、 **ソース テーブルおよびビュー**ページし、の名前を入力、**新しい**テーブルに、**先**列です。  

## <a name="what-about-existing-data-in-the-destination"></a>マップ先の既存のデータについて説明します。
![列マッピング ページのオプション](../../integration-services/import-export-data/media/column-mappings-page-options-section.png)

 **変換先テーブル/ファイル内の行を削除する**  
 新しいデータを読み込む前に、既存のテーブルからデータを削除するかどうかを指定します。  
  
 **変換先テーブル/ファイルに行を追加する**  
 既存のテーブルに存在するデータに、新しいデータを追加するかどうかを指定します。  
  
 **変換先テーブルを削除した後、再作成する**  
 変換先テーブルを上書きします。 このオプションは変換先テーブルを作成するウィザードを使用する場合にのみ使用できます。 ウィザードによって作成されたパッケージを保存し、その後パッケージを再び実行すると、変換先テーブルは削除されて、再作成されます。 これは、設定を複数回テストする場合に便利なオプションです。
  
 **ID 挿入を許可する**  
 変換元データの既存の ID 値を変換先テーブルの ID 列に挿入します。 既定では、変換先の ID 列に対して挿入は通常許可されません。  
  
> [!TIP]
> 既存のプライマリ キーが id 列、autonumber 列、または同等の列である場合、既存のプライマリ キー値を保持するには、通常、このオプションを選択する必要があります。  その他の場合、変換先の ID 列には通常、新しい値が割り当てられます。  

## <a name="keep-your-autonumber-or-identity-values"></a>オート ナンバーまたは id の値を保持します。
あり、autonumber 列または id 列のデータをエクスポートする場合などの Microsoft Access からエクスポートしている場合を確認を選択することを確認して**id の挿入を有効にする**上ですぐに説明したようです。

## <a name="review-column-mappings"></a>列マッピングを確認します。
![列マッピング ページのマッピング セクション](../../integration-services/import-export-data/media/column-mappings-page-mappings-section.png)

 **マッピング**  
 データ ソースの各列が変換先の列にどのようにマップされるかを表示します。
 
**[マッピング]** の一覧には、次の列があります。  
  
-    **ソース**  
     各ソース列を表示します。  
  
-   **変換先**  
    マップされる変換先列を確認するか、別の列を選択します。
    
    ソース テーブルからすべての列をコピーする必要はありません。 コピーしない列については、 **[変換先]** を選択すると、列のサブセットのみをコピーできます。 列をマップする前に、マップされないすべての列を無視する必要があります。  
  
-   **種類**  
    変換先列のデータ型を確認するか、別のデータ型を選択します。
  
-   **NULL 値の使用**  
    変換先列に null 値を使用できるかどうかを指定します。  
  
-   **サイズ**  
    変換先列の文字数を指定します (該当する場合)。  
  
-    **[精度]**  
    該当する場合は、変換先列には、数字の数の数値データの有効桁数を指定します。  
  
 -   **[スケール]**  
    該当する場合は、変換先列には、小数点数の数値データの小数点以下桁数を指定します。  
  
## <a name="whats-next"></a>次の操作  
 確認して、ソース列からコピーしたデータを受信し、をクリックする変換先列を構成した後**OK**、**列マッピング** ダイアログ ボックスに戻ります、**ソースの選択テーブルとビュー**ページまたは、**フラット ファイル変換先の構成**ページ。 詳細については、「 [[コピー元のテーブルおよびビューを選択]](../../integration-services/import-export-data/select-source-tables-and-views-sql-server-import-and-export-wizard.md) 」または「 [[フラット ファイルの変換先の構成]](../../integration-services/import-export-data/configure-flat-file-destination-sql-server-import-and-export-wizard.md)」を参照してください。  
  
 指定したマッピングが **[マッピング]** 一覧で成功しない可能性がある場合は、 **[列マッピング]** ダイアログ ボックスに **[データ型マッピングの確認]** ページが表示されます。 このページでは、警告を確認し、変換オプションを指定して、エラーの処理方法も指定します。 詳しくは、「 [[データ型マッピングの確認]](../../integration-services/import-export-data/review-data-type-mapping-sql-server-import-and-export-wizard.md)」をご覧ください。  
 
 ## <a name="see-also"></a>参照
[SQL Server インポートおよびエクスポート ウィザードのデータ型マッピング](../../integration-services/import-export-data/data-type-mapping-in-the-sql-server-import-and-export-wizard.md)  
[簡単な例によるインポートおよびエクスポート ウィザードの概要](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)


