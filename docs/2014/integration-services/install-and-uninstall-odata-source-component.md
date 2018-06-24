---
title: インストールし、OData ソース コンポーネントをアンインストール |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0a3ae788-e8c8-4a4d-bb15-34c673abcd17
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: ae48af3dec0be31d329548cbc0d7cd76007dacaf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36073044"
---
# <a name="install-and-uninstall-odata-source-component"></a>OData ソース コンポーネントのインストールと、アンインストール
  このトピックでは、コンピューターに OData ソース コンポーネントをインストールまたは削除する手順について説明します。  
  
## <a name="installation"></a>インストール  
 OData ソース コンポーネントを使用するには、前提条件となる次のコンポーネントをコンピューターにインストールしておく必要があります。  
  
-   SQL Server データ ツール (パッケージの設計用)  
  
-   SQL Server Integration Services (Visual Studio の外部でのパッケージ実行用)  
  
 OData ソース コンポーネントをインストールするには、ダウンロード[SQL Server 2014 Feature Pack](http://go.microsoft.com/fwlink/p/?LinkId=391999)次の MSI ファイルのいずれかを実行します。  
  
-   64 ビット プラットフォームでは ODataSourceForSQLServer2014-amd64.msi  
  
-   32 ビット プラットフォームでは ODataSourceForSQLServer2014-x86.msi  
  
> [!IMPORTANT]  
>  64 ビット インストーラーは、OData ソース コンポーネントの 32 ビット版と 64 ビット版の両方をインストールします。 32 ビット インストーラーを実行する必要があるのは、32 ビット OS を使用している場合のみです。  
  
## <a name="uninstallation"></a>アンインストール  
 OData ソース コンポーネントをアンインストールしてから、**プログラムと機能**メニュー。 検索、 **Microsoft SQL Server SSIS OData ソース コンポーネント (x64)** エントリとクリック**アンインストール**です。  
  
  