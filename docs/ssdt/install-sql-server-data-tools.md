---
title: SQL Server Data Tools のインストール | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- sql.data.tools.package.stub
ms.assetid: 6f8616cb-9119-42c3-a9b1-936e088763e7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3a847748b0f0025402da1feb794f5c441ea2a3f5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47773570"
---
# <a name="install-sql-server-data-tools"></a>SQL Server Data Tools のインストール
このトピックでは、 SQL Server Data Tools のインストール方法について説明します。 SQL Server Data Tools の更新は、SQL Server Data Tools ダウンロード ページ ([最新の SQL Server Data Tools をインストール](http://go.microsoft.com/fwlink/?LinkID=616714)) で入手できます。  
  
Visual Studio 2012 と Visual Studio 2013 のどちらを使用しているかに関係なく、SQL Server Data Tools の最新の更新プログラムをインストールして最新機能を入手してください。  
  
## <a name="sql-server-data-tools-for-visual-studio-2013"></a>Visual Studio 2013 用 SQL Server Data Tools  
SQL Server Data Tools は、Visual Studio 2013 Express for Web、Visual Studio 2013 Express for Desktop、Visual Studio Community 2013、および Professional SKU 以上のすべての有料 SKU に含まれています。 Visual Studio 2013 をインストールして、[ツール]、[拡張機能と更新プログラム]、[更新プログラム] の順に選択すると、インストールできる更新プログラムがあるかどうかを確認できます。  
  
## <a name="sql-server-data-tools-for-visual-studio-2012"></a>Visual Studio 2012 用 SQL Server Data Tools  
SQL Server Data Tools は、Visual Studio 2012 の Professional 以上の SKU で提供されます。 Visual Studio 2012 をインストールして 2012 年 11 月以降の SQL Server Data Tools 更新プログラムをインストールすると、 SQL Server Data Tools は、インストールする更新プログラムが存在する場合に報告できます。 詳しくは、「[[更新の確認] ダイアログ ボックス](../ssdt/check-for-updates-dialog-box.md)」をご覧ください。  
  
Visual Studio 2012 がインストールされていない場合、SQL Server Data Tools は Visual Studio 2012 統合シェルをインストールして SQL Server Data Tools をインストールします。  
  
## <a name="administrative-installation-point"></a>管理インストール ポイント  
複数のコンピューターや、インターネットにアクセスできないコンピューターに SQL Server Data Tools をインストールする必要がある場合は、ネットワーク共有か物理メディアに管理インストール レイアウトを作成し、そのインストール ポイントからインストールできます。  
  
インストール レイアウトを作成するには、SSDTSetup.EXE をダウンロードして、 `/layout`*location* オプションを使用して実行し、 *location*にレイアウトを作成します。 その後で、ユーザーは *location*から SSDTSetup.Exe を実行できます。  
  
SSDTSetup.exe をダウンロードするには、 [[最新の SQL Server Data Tools をインストール]](http://go.microsoft.com/fwlink/?LinkID=616714)にアクセスし、ご利用のバージョンの Visual Studio に対応したリンクをクリックして、使用している言語に応じた SSDTSetup.exe をダウンロードします。  
  
