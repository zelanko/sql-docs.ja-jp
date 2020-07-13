---
title: Azure SQL Database への接続 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsqlazure.f1
ms.assetid: 4e0344e9-1822-4698-ad22-05f1f341ced7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 73b15dd890f9bd6e00d61fa0507546c561425d8a
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84527048"
---
# <a name="connect-to-an-azure-sql-database-ssas"></a>Azure SQL データベースへの接続 (SSAS)
  **テーブルのインポート ウィザード** のこのページを使用すると、 [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)]に接続できます。 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]からウィザードにアクセスするには、 **[モデル]** メニューの **[データ ソースからのインポート]** をクリックします。  
  
> [!NOTE]  
>  Azure DataMarket データセットに接続している場合は、「[レポートまたはデータ フィードへの接続 (SSAS)](connect-to-a-report-or-data-feed-ssas.md)」を参照してください。  
  
 [!INCLUDE[ssSDS](../includes/sssds-md.md)] は、SQL Server 認証を使用して接続するホスト型のリレーショナル データベースです。 [!INCLUDE[ssSDS](../includes/sssds-md.md)]の詳細については、 [SQL データベース](https://go.microsoft.com/fwlink/?LinkID=157856)の Web サイトを参照してください。 データ ソースに接続するには、適切なプロバイダーがコンピューターにインストールされている必要があります。  
  
> [!NOTE]  
>  このページでデータベースを選択する際には、現在のユーザーの資格情報が使用されます。 ただし、[権限借用情報] ページで指定されたユーザーに、選択したデータベースの読み取り権限がないと、インポートは成功しません。  
  
## <a name="ui-element-list"></a>UI 要素の一覧  
 **[接続の表示名]**  
 このデータ ソース接続の一意の名前を入力します。 これは必須フィールドです。  
  
 **サーバー名**  
 接続するサーバーの名前または IP アドレスを入力します。  
  
 **ユーザー名**  
 データベース接続に使用するユーザー名を指定します。  
  
 このユーザー名は、データ ソースの接続文字列を構築するときに使用されます。 [テーブルのプロパティ] ウィンドウおよびインポート ウィザードでデータのプレビューまたはフィルター処理を行う際も、これらの資格情報が使用されます。 データをインポートまたは更新する際には、これらの資格情報は使用されず、[権限借用情報] ページで指定された Windows の資格情報が使用されます。  
  
 **パスワード**  
 データベース接続に使用するパスワードを指定します。  
  
 **[パスワードを保存する]**  
 **[パスワード]** ボックスに入力したパスワードを保存するかどうかを指定します。  
  
 **データベース名**  
 データベースを一覧から選択します。  
  
 **詳細設定**  
 **[詳細プロパティの設定]** ダイアログ ボックスを使用して追加の接続プロパティを設定します。 詳細については、「[[詳細プロパティの設定] (SSAS)](set-advanced-properties-ssas.md)」を参照してください。  
  
 **接続をテスト**  
 現在の設定を使用して、データ ソースに対する接続の確立を試みます。 接続が正常に確立されたかどうかを示すメッセージが表示されます。  
  
  
