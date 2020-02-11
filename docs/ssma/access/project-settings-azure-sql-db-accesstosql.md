---
title: プロジェクトの設定 (Azure SQL DB) (データベースの設定) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Project Settings dialog box, SQL Azure
- SQL Azure settings
ms.assetid: bbb8a204-d0e4-4f0b-9709-271feb1f136e
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 60140559f94cdeebea935b423fbbeef24bce7a08
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67929466"
---
# <a name="project-settings-azure-sql-db-accesstosql"></a>プロジェクトの設定 (Azure SQL DB) (Sql server による)
SQL Azure プロジェクトの設定を使用すると、接続ダイアログに追加する SQL Azure データベースサフィックスを構成し、SQL Azure 接続でハートビートメカニズムを実装することもできます。  
  
SQL Azure ウィンドウは、[プロジェクトの**設定**] ダイアログボックスと [**既定のプロジェクトの設定**] ダイアログボックスで使用できます。  
  
-   [プロジェクトの設定] ダイアログボックスを使用すると、現在のプロジェクトの構成オプションを設定できます。 SQL Azure 設定にアクセスするには、[**ツール**] メニューの [**プロジェクトの設定**] を選択し、左側のウィンドウの下部にある [**全般**] をクリックして、[ **SQL Azure**] を選択します。  
  
-   [既定のプロジェクトの設定] ダイアログボックスを使用すると、すべてのプロジェクトの構成オプションを設定できます。 SQL Azure 設定にアクセスするには、[**ツール**] メニューの [ **Defaultproject の設定**] を選択し、[**移行先のバージョン**] コンボボックスで [SQL Azure] としてプロジェクトの種類を選択して SQL Azure ウィンドウの設定にアクセスします。次に、左側のウィンドウの下部にある [**全般**] をクリックし、[ **SQL Azure**] を選択します。  
  
## <a name="options"></a>オプション  
  
## <a name="connectivity"></a>接続  
**［ハートビートの間隔］**  
  
SQL Azure 接続を ' 分: seconds ' 形式で保持するハートビートメカニズムに使用する時間間隔を指定します。  
  
**既定値**: ' 4:45 '  
  
値は、' m:ss ' 形式 (たとえば、' 4:45 ' または ' 0:50 ') で指定する必要があります。  
  
**SQL Azure サーバーサフィックス**  
  
SQL Azure サーバーのサフィックスを指定します  
  
**既定値**: ' database.windows.net '。  
  
