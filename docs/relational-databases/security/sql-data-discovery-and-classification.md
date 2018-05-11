---
title: SQL データの検出と分類 | Microsoft Docs
description: SQL データの検出と分類
documentationcenter: ''
author: giladm
manager: shaik
ms.reviewer: carlrab
ms.assetid: 89c2a155-c2fb-4b67-bc19-9b4e03c6d3bc
ms.service: sql-database
ms.prod_service: sql-database,sql
ms.custom: security
ms.tgt_pltfrm: na
ms.topic: article
ms.date: 02/13/2018
ms.author: giladm
ms.openlocfilehash: 8900faccfda82e759ee6f31009682eb632df7509
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sql-data-discovery-and-classification"></a>SQL データの検出と分類
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

データの検出と分類では、データベース内の機密データの**検出**、**分類**、**ラベル付け** & **レポート作成**を行うための新しいツールが導入されました。このツールは SQL Server Management Studio (SSMS) に組み込まれています。
最も機密性の高いデータ (ビジネス、財務、医療、PII など) の検出と分類は、組織の情報保護の達成において極めて重要な役割を果たすことができます。 次のような場合にインフラストラクチャとして使用できます。
* データのプライバシー基準と規制のコンプライアンス要件 (GDPR など) を満たせるようにする。
* 機密性の高いデータを含むデータベース/列へのアクセスを制御し、セキュリティを強化する。


> [!NOTE]
> データの検出と分類は、**SQL Server 2008 以降でサポート**されます。 Azure SQL Database については、「[Azure SQL Database のデータの検出と分類](https://go.microsoft.com/fwlink/?linkid=866265)」を参照してください。

## <a id="subheading-1"></a>概要
データの検出と分類では高度な一連のサービスが導入され、データベースだけでなく、データの保護を目的とした新しい SQL Information Protection パラダイムが形成されます。
* **検出および推奨事項** – 分類エンジンはデータベースをスキャンし、機密データが含まれる可能性のある列を識別します。 適切な分類の推奨事項を確認して適用するだけでなく、手動で列を分類するための簡単な方法が提供されます。
* **ラベル付け** – 列で永続的に機密分類ラベルにタグを付けることができます。
* **表示** - データベース分類状態を詳細なレポートに表示することができます。このレポートを印刷したりエクスポートしたりして、コンプライアンスと監査の目的に、またその他のニーズに合わせて使用することができます。

## <a id="subheading-2"></a>機微な列の検出、分類およびラベル付け
次のセクションでは、データベース内の機密データを含む列の検出、分類、およびラベル付けの手順に加え、データベースの現在の分類状態の表示とレポートのエクスポートの手順について説明します。

分類には、次の 2 つのメタデータ属性が含まれます。
* ラベル – 列に格納されるデータの機密レベルを定義するために使用される、主な分類属性です。  
* 情報の種類 – 列に格納されるデータの種類をさらに細分化します。

<br>
**SQL Server データベースを分類するには:**

1. SQL Server Management Studio (SSMS) で、SQL Server に接続します。

2. SSMS オブジェクト エクスプローラーで、分類するデータベースを右クリックして、**[タスク]** > **[データの分類]** の順に選択します。

    ![ナビゲーション ウィンドウ][1]

3. 分類エンジンは機密データが含まれる可能性のある列についてデータベースをスキャンし、**推奨される列の分類**のリストを提供します。

    * 推奨される列の分類のリストを表示するには、上部にある推奨事項通知ボックスまたはウィンドウの下部にある推奨事項パネルをクリックします。

        ![ナビゲーション ウィンドウ][2]

        ![ナビゲーション ウィンドウ][3]

    * 推奨事項のリストを確認します。
        * 特定の列の推奨事項を承諾するには、関連する行の左側の列のチェック ボックスをオンにします。 推奨事項テーブル ヘッダーのチェック ボックスをオンにして、*すべての推奨事項* を承諾済みとしてマークすることもできます。

        * ドロップダウン ボックスを使用して、推奨される情報の種類と機密ラベルを変更することもできます。        

        ![ナビゲーション ウィンドウ][4]

    * 選択した推奨事項を適用するには、青い **[Accept selected recommendations]\(選択した推奨事項を承諾\)** ボタンをクリックします。

        ![ナビゲーション ウィンドウ][5]

4. 代わりに列を**手動で分類**することもできます。さらに、推奨事項ベースの分類について、次の操作を実行することもできます。

    * ウィンドウの上部のメニューで **[分類の追加]** をクリックします。

        ![ナビゲーション ウィンドウ][6]

    * 開いたコンテキスト メニューで、分類するスキーマ、テーブル、列の順に選択し、情報の種類と機密ラベルを選択します。 次に、コンテキスト ウィンドウの下部にある青い **[分類の追加]** ボタンをクリックします。

        ![ナビゲーション ウィンドウ][7]

5. 分類を完了し、新しい分類メタデータでデータベース列に永続的にラベル (タグ) を付けるには、ウィンドウの上部のメニューで **[保存]** をクリックします。

    ![ナビゲーション ウィンドウ][8]


6. データベースの分類状態の完全な要約を示すレポートを生成するには、ウィンドウの上部のメニューで **[レポートの表示]** をクリックします。

    ![ナビゲーション ウィンドウ][9]

    ![ナビゲーション ウィンドウ][10]


## <a id="subheading-3"></a>次の手順

Azure SQL Database については、「[Azure SQL Database のデータの検出と分類](https://go.microsoft.com/fwlink/?linkid=866265)」を参照してください。

次の列レベルのセキュリティ メカニズムを適用して、機微な列の保護を検討してください。

* [動的データ マスク](https://docs.microsoft.com/en-us/sql/relational-databases/security/dynamic-data-masking): 使用中の機微な列を難読化します。
* [Always Encrypted](https://docs.microsoft.com/en-us/sql/relational-databases/security/encryption/always-encrypted-database-engine): 保存中の機微な列を暗号化します。

<!--Anchors-->
[SQL Data Discovery & Classification overview]: #subheading-1
[Discovering, classifying & labeling sensitive columns]: #subheading-2
[Next Steps]: #subheading-3

<!--Image references-->
[1]: ./media/sql-data-discovery-and-classification/1_data_classification_explorer_menu.png
[2]: ./media/sql-data-discovery-and-classification/2_recommendations_notification_box.png
[3]: ./media/sql-data-discovery-and-classification/3_recommendations_panel.png
[4]: ./media/sql-data-discovery-and-classification/4_recommendations.png
[5]: ./media/sql-data-discovery-and-classification/5_accept_recommendations_button.png
[6]: ./media/sql-data-discovery-and-classification/6_add_classification_button.png
[7]: ./media/sql-data-discovery-and-classification/7_manual_classification.png
[8]: ./media/sql-data-discovery-and-classification/8_save.png
[9]: ./media/sql-data-discovery-and-classification/9_view_report.png
[10]: ./media/sql-data-discovery-and-classification/10_report.png
