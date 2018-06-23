---
title: アップグレード アドバイザーのインストール |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installing Upgrade Advisor
- Setup [Upgrade Advisor]
- Upgrade Advisor [SQL Server], installing
ms.assetid: 1b7d6eca-1df1-47df-bbba-0fc485706a95
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6cde30d3dd12f6f072d4cb83f869700c7357484f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164231"
---
# <a name="installing-upgrade-advisor"></a>アップグレード アドバイザーのインストール
  インストールする場合、SQL Server 2014 アップグレード アドバイザーは、新機能は、分析対象によって異なります。 アップグレード アドバイザーでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のすべての [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンポーネントをリモートで分析できます。 インスタンスをスキャンしない場合[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]に接続できる任意のコンピューターでアップグレード アドバイザーをインストールすることができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、一致して、[アップグレード アドバイザーの前提条件](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)です。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインスタンスをスキャンする場合は、アップグレード アドバイザーをレポート サーバーにインストールする必要があります。  
  
 実行、 **SQLUA.msi**アップグレード アドバイザーをインストールするファイル。 コマンド プロンプトからインストールすると、自動インストールを実行できます。 参照してください[コマンド プロンプトからアップグレード アドバイザーをインストールする](../../../2014/sql-server/install/installing-upgrade-advisor-from-the-command-prompt.md)構文と例についてはします。  
  
 SQLUA.msi の入手先:  
  
-   **Redist**のフォルダー、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]製品メディア。  
  
-   一部として、 [SQL 2014 Feature Pack ダウンロード](http://www.microsoft.com/download/details.aspx?id=42295)です。  
  
## <a name="uninstalling-upgrade-advisor"></a>アップグレード アドバイザーのアンインストール  
 アップグレード アドバイザーをアンインストールするを使用**プログラム追加と削除**です。 コマンド プロンプトの構文でも、削除またはアンインストール操作がサポートされます。  
  
  