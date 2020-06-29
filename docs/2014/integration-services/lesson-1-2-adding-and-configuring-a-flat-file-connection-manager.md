---
title: '手順 2: フラット ファイル接続マネージャーの追加と構成 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9a77dd32-d8c2-4961-ad37-2a971f9d6043
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d07502256418b1d528f73bac3296045c393ddc1b
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85436119"
---
# <a name="step-2-adding-and-configuring-a-flat-file-connection-manager"></a>手順 2:フラット ファイル接続マネージャーの追加と構成
  この実習では、先ほど作成したパッケージにフラット ファイル接続マネージャーを追加します。 パッケージにフラット ファイル接続マネージャーを追加すると、フラット ファイルからデータを抽出できるようになります。 フラット ファイル接続マネージャーでは、フラット ファイルからデータを抽出するときに適用するファイルの名前と場所、ロケールとコード ページ、およびファイル形式を指定できます。また、列区切り記号も指定できます。 さらに、各列のデータ型を手動で指定できます。 **[列の型の予測]** ダイアログ ボックスを使用して、抽出したデータの列を [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] データ型に自動的にマップすることもできます。  
  
 通常は、操作する各フラット ファイルについて、新しいファイル インポート マネージャーを作成する必要があります。 ただし、このチュートリアルでは、データ形式がまったく同じである複数のフラット ファイルからデータを抽出するので、フラット ファイル接続マネージャーを 1 つだけパッケージに追加して、構成します。  
  
 このチュートリアルでは、フラット ファイル接続マネージャーで次のプロパティを構成します。  
  
-   **列名:** フラット ファイルには列名がないため、フラット ファイル接続マネージャーによって既定の列名が作成されます。 これらの既定の列名は、各列の内容を明確に表していません。 わかりやすい名前にするには、既定の列名を変更し、フラット ファイル データの読み込み先であるファクト テーブルと一致する名前を付ける必要があります。  
  
-   **データのマッピング:** フラット ファイル接続マネージャーのデータ型マッピングを指定します。このマッピングは、その接続マネージャーを参照するすべてのフラット ファイル データ ソース コンポーネントで使用されます。 フラット ファイル接続マネージャーでは、データ型を手動でマップできます。また、 **[列の型の予測]** ダイアログ ボックスを使用してマップすることもできます。 このチュートリアルでは、 **[列の型の予測]** ダイアログ ボックスで予測されたマッピングを表示し、 **[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスで必要なマッピングを手動で行います。  
  
 フラット ファイル接続マネージャーでは、データ ファイルに関するロケール情報が提供されます。 コンピューターが、地域オプション [英語 (米国) を使用するように構成されていない場合は、[**フラットファイル接続マネージャーエディター** ] ダイアログボックスで追加のプロパティを設定する必要があります。  
  
### <a name="to-add-a-flat-file-connection-manager-to-the-ssis-package"></a>SSIS パッケージにフラット ファイル接続マネージャーを追加するには  
  
1.  **[接続マネージャー]** 領域内を右クリックし、 **[新しいフラット ファイル接続]** をクリックします。  
  
2.  **[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスで、 **[接続マネージャー名]** に「 **Sample Flat File Source Data**」と入力します。  
  
3.  **[参照]** をクリックします。  
  
4.  **[ファイルを開く]** ダイアログ ボックスで、コンピューター上の SampleCurrencyData.txt ファイルを指定します。  
  
     このサンプル データは、 [!INCLUDE[ssIS](../includes/ssis-md.md)] のレッスン パッケージに含まれています。 サンプル データとレッスン パッケージをダウンロードするには、次の手順を実行します。  
  
    1.  「 [Integration Services 製品サンプル](https://go.microsoft.com/fwlink/?LinkId=275027)」に移動します。  
  
    2.  [**ダウンロード**] タブをクリックします。  
  
    3.  SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip ファイルをクリックします。  
  
5.  [先頭データ行を列名として使用する] チェック ボックスをオフにします。  
  
### <a name="to-set-locale-sensitive-properties"></a>ロケール依存型のプロパティを設定するには  
  
1.  **[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスで、 **[全般]** をクリックします。  
  
2.  **ロケール**を英語 (米国) に設定し、**コードページ**を1252に設定します。  
  
### <a name="to-rename-columns-in-the-flat-file-connection-manager"></a>フラット ファイル接続マネージャーで列名を変更するには  
  
1.  **[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスで、 **[詳細設定]** をクリックします。  
  
2.  プロパティ ペインで、次のように変更します。  
  
    -   **列 0**の name プロパティをに変更し `AverageRate` ます。  
  
    -   **列 1**の name プロパティをに変更 `CurrencyID` します。  
  
    -   **列 2**の name プロパティをに変更 `CurrencyDate` します。  
  
    -   **列 3**の name プロパティをに変更 `EndOfDayRate` します。  
  
    > [!NOTE]  
    >  既定では、4 つのすべての列が文字列データ型 [DT_STR] に設定され、`OutputColumnWidth` は 50 に設定されます。  
  
### <a name="to-remap-column-data-types"></a>列のデータ型を再マップするには  
  
1.  **[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスで、 **[型の推測]** をクリックします。  
  
     [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] は、最初の 200 行分のデータに基づいて最適なデータ型を自動的に予測します。 この推測オプションを変更して、サンプルの行数を変更したり、整数またはブール データの既定のデータ型を指定したり、文字列の列の余白としてスペースを挿入することもできます。  
  
     ここでは **[列の型の予測]** ダイアログ ボックスのオプションを変更せずに、 **[OK]** をクリックして [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] に列のデータ型を予測させます。 これにより、 **[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスの **[詳細設定]** ペインに戻ります。このペインでは、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]によって予測された列のデータ型を確認できます ( **[キャンセル]** をクリックすると、列のメタデータの予測は行われず、既定の文字列データ型 (DT_STR) が使用されます)。  
  
     このチュートリアルでは、SampleCurrencyData.txt ファイルのデータに対応するデータ型を [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] が推測します。推測されたデータ型は、下表の 2 列目に示されています。 一方、変換先の列に必要なデータ型 (以降の手順で定義します) は、下表の 4 列目に示されています。  
  
    |フラット ファイルの列|推測されたデータ型|変換先列|変換先の型|  
    |----------------------|--------------------|------------------------|----------------------|  
    |AverageRate|float [DT_R4]|FactCurrency.AverageRate|float|  
    |CurrencyID|string [DT_STR]|DimCurrency,CurrencyAlternateKey|nchar(3)|  
    |CurrencyDate|date [DT_DATE]|DimDate.FullDateAlternateKey|date|  
    |EndOfDayRate|float [DT_R4]|FactCurrency.EndOfDayRate|float|  
  
     列に対して提案されたデータ型 `CurrencyID` は、変換先テーブルのフィールドのデータ型と互換性がありません。 のデータ型 `DimCurrency.CurrencyAlternateKey` は nchar (3) であるため、を `CurrencyID` 文字列 [DT_STR] から文字列 [DT_WSTR] に変更する必要があります。 また、フィールド `DimDate.FullDateAlternateKey` は date データ型として定義されているため、を `CurrencyDate` date [DT_Date] からデータベース日付 [DT_DBDATE] に変更する必要があります。  
  
2.  一覧で、CurrencyID 列を選択し、プロパティペインで、列のデータ型を `CurrencyID` 文字列 [DT_STR] から Unicode 文字列 [DT_WSTR] に変更します。  
  
3.  プロパティペインで、 `CurrencyDate` date [DT_DATE] のデータ型を [データベースの日付 [DT_DBDATE] に変更します。  
  
4.  **[OK]** をクリックします。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [手順 3:OLE DB 接続マネージャーの追加と構成](lesson-1-3-adding-and-configuring-an-ole-db-connection-manager.md)  
  
## <a name="see-also"></a>関連項目  
 [フラットファイル接続マネージャー](connection-manager/file-connection-manager.md)   
 [Integration Services のデータ型](data-flow/integration-services-data-types.md)  
  
  
