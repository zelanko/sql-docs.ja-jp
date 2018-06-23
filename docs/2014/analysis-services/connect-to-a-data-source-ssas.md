---
title: データ ソース (SSAS) への接続 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.bidtoolset.conndatasource.f1
ms.assetid: 1e2b17e9-092b-4af1-8a58-c52b8fe10ff1
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: f33af08d91f2c8e739c9295daed0ae47563ede51
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077230"
---
# <a name="connect-to-a-data-source-ssas"></a>[データ ソースへの接続] (SSAS)
  **テーブルのインポート ウィザード** のこのページを使用すると、リレーショナル データベース、データ フィード、ファイルなど、さまざまなデータ ソースに対する新しいデータ ソース接続を作成できます。 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]からウィザードにアクセスするには、 **[モデル]** メニューの **[データ ソースからのインポート]** をクリックします。  
  
 データ ソースに接続するには、適切なプロバイダーがコンピューターにインストールされている必要があります。 また、ワークスペースのデータベース サーバーにも適切なプロバイダーがインストールされている必要があります。 32 ビット (x86) サーバーの場合は、32 ビット プロバイダーがインストールされている必要があります。 64 ビット (x64) サーバーの場合は、64 ビット プロバイダーがインストールされている必要があります。  
  
 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 常に、アーキテクチャに関係なく、32 ビット プロセスで実行されます。 64 ビット コンピューターで [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] を実行している場合は、データ プロバイダーをインストールする際に、次の点に注意が必要です。  
  
-   32 ビットと 64 ビットのサイド バイ サイド インストールをサポートするプロバイダーの場合は、両方のプロバイダーをインストールする必要があります。  
  
-   ACE プロバイダーの場合は、64 ビット バージョンのプロバイダーをインストールする必要があります。 ACE プロバイダーは Office によって自動的にインストールされるため、ワークスペース データベース サーバーをホストする 64 ビット コンピューターでは 32 ビット バージョンの Microsoft Office を実行しないでください。  
  
     ACE プロバイダーは、テキスト ファイル、Excel ファイル、および Access ファイルからのインポートに使用されます。 これらのデータ ソースをサポートする必要がない場合は、64 ビットのワークスペース データベース サーバーが実行されているコンピューターで、32 ビット バージョンの Microsoft Office を実行してもかまいません。  
  
-   32 ビットと 64 ビットのサイド バイ サイド インストールをサポートしないその他のプロバイダーについては、32 ビットのプロバイダーをインストールする必要があります。 64 ビット コンピューターしか利用できない場合は、ワークスペース データベース サーバーとして 64 ビットのプロバイダーがインストールされたリモート コンピューターを使用してください。  
  
  