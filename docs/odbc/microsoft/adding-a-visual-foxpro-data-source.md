---
title: Visual FoxPro データ ソースの追加 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro data source [ODBC], adding
- adding data sources [ODBC], Visual FoxPro ODBC driver
ms.assetid: 1487e188-52c8-4f48-b4fe-25a650dd9e97
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8d59ad4b7663202b0ca66fc0eabb4ad6405760d8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="adding-a-visual-foxpro-data-source"></a>Visual FoxPro データ ソースを追加します。
Visual FoxPro データ、アプリケーションからにアクセスするには、データ ソースが必要です。 次のように、データ ソースを作成できます。  
  
-   Microsoft® Word、Excel、または Microsoft Access などのアプリケーションでは、ODBC ドライバーを使用します。  
  
-   、アプリケーションの外部には、Microsoft Windows® 95、Windows 98、または Microsoft Windows/Windows 2000 のコントロール パネルを使用します。  
  
 データ ソースは、システムに存在、後に、Visual FoxPro データにアクセスするたびに、同じデータ ソース再を利用できます。 いくつかの異なるデータベースまたはテーブルにアクセスする場合は、データベースまたはディレクトリごとに個別のデータ ソースを作成することができます。  
  
 次の手順では、コントロール パネルを使用して、データ ソースを作成します。 アプリケーションからデータ ソースを作成する方法の詳細については、次を参照してください。[から Microsoft Office Visual FoxPro データにアクセスする](../../odbc/microsoft/accessing-visual-foxpro-data-from-microsoft-office.md)です。  
  
### <a name="to-add-a-visual-foxpro-data-source"></a>Visual FoxPro データ ソースを追加するには  
  
1.  Windows 2000 を実行しているコンピューターで、Windows コントロール パネルを開くし、管理ツール をダブルクリックします。  
  
2.  ODBC データ ソース アドミニストレーター ダイアログ ボックスを開くデータ ソース (ODBC) をダブルクリックします。 このアイコンは、Visual FoxPro ODBC ドライバーまたは ODBC ドライバー ソフトウェアをインストールした後に使用できます。  
  
    > [!NOTE]  
    >  以前のバージョンの Windows を実行している場合は、Windows コントロール パネルを開き 32 ビット ODBC と ODBC を開くには、ODBC データ ソース アドミニストレーター ダイアログ ボックスをダブルクリックします。  
  
3.  [追加] をクリックします。  
  
4.  データ ソースの新規作成 ダイアログ ボックスで、Microsoft Visual FoxPro ドライバーを選択し、完了 をクリックします。  
  
5.  [ODBC Visual FoxPro セットアップ ダイアログ ボックス](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)、データ ソースの名前と説明を入力、データベースの種類を選択して、データベースまたはディレクトリを選択およびし、[OK] をクリックします。  
  
     新しいデータ ソース名は、ODBC データ ソース アドミニストレーター ダイアログ ボックスの ユーザー DSN タブでユーザー データ ソース ボックスに表示されます。  
  
6.  新しいデータ ソースを保存し、ODBC データ ソース アドミニストレーター ダイアログ ボックスを閉じるには、ok をクリックします。
