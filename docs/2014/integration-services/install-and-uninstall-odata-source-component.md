---
title: OData ソースコンポーネントのインストールとアンインストール |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0a3ae788-e8c8-4a4d-bb15-34c673abcd17
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c22c7c88e57c354b92bcb69429a9ab6c06ca368d
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85436579"
---
# <a name="install-and-uninstall-odata-source-component"></a>OData ソース コンポーネントのインストールと、アンインストール
  このトピックでは、コンピューターに OData ソース コンポーネントをインストールまたは削除する手順について説明します。  
  
## <a name="installation"></a>インストール  
 OData ソース コンポーネントを使用するには、前提条件となる次のコンポーネントをコンピューターにインストールしておく必要があります。  
  
-   SQL Server データ ツール (パッケージの設計用)  
  
-   SQL Server Integration Services (Visual Studio の外部でのパッケージ実行用)  
  
 OData ソースコンポーネントをインストールするには、 [SQL Server 2014 Feature Pack](https://go.microsoft.com/fwlink/p/?LinkId=391999)をダウンロードし、次の MSI ファイルのいずれかを実行します。  
  
-   64 ビット プラットフォームでは ODataSourceForSQLServer2014-amd64.msi  
  
-   32 ビット プラットフォームでは ODataSourceForSQLServer2014-x86.msi  
  
> [!IMPORTANT]  
>  64 ビット インストーラーは、OData ソース コンポーネントの 32 ビット版と 64 ビット版の両方をインストールします。 32 ビット インストーラーを実行する必要があるのは、32 ビット OS を使用している場合のみです。  
  
## <a name="uninstallation"></a>アンインストール  
 OData ソースコンポーネントをアンインストールするには、[**プログラムと機能**] メニューを使用します。 **MICROSOFT SQL SERVER SSIS OData ソースコンポーネント (x64)** のエントリを見つけて、[**アンインストール**] をクリックします。  
  
  
