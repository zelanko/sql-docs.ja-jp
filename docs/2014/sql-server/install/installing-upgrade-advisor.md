---
title: アップグレード アドバイザーのインストール |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- Setup [Upgrade Advisor]
- Upgrade Advisor [SQL Server], installing
ms.assetid: 1b7d6eca-1df1-47df-bbba-0fc485706a95
caps.latest.revision: 34
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a8c15c361f1fc29a805948b3761fd0a04c5c396c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37327012"
---
# <a name="installing-upgrade-advisor"></a>アップグレード アドバイザーのインストール
  インストールする場合、SQL Server 2014 アップグレード アドバイザーは、どのようなは、分析対象によって異なります。 アップグレード アドバイザーでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のすべての [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンポーネントをリモートで分析できます。 インスタンスをスキャンしない場合[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]に接続できる任意のコンピューターでアップグレード アドバイザーをインストールする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、かつを満たす、[アップグレード アドバイザーの前提条件](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)します。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインスタンスをスキャンする場合は、アップグレード アドバイザーをレポート サーバーにインストールする必要があります。  
  
 実行、 **SQLUA.msi**アップグレード アドバイザーをインストールするファイル。 コマンド プロンプトからインストールすると、自動インストールを実行できます。 参照してください[コマンド プロンプトからアップグレード アドバイザーをインストールする](../../../2014/sql-server/install/installing-upgrade-advisor-from-the-command-prompt.md)構文と例についてはします。  
  
 SQLUA.msi の入手先:  
  
-   **Redist**のフォルダー、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]製品メディア。  
  
-   一部として、 [SQL 2014 Feature Pack ダウンロード](http://www.microsoft.com/download/details.aspx?id=42295)します。  
  
## <a name="uninstalling-upgrade-advisor"></a>アップグレード アドバイザーのアンインストール  
 使用してアップグレード アドバイザーをアンインストールする**プログラム追加と削除**します。 コマンド プロンプトの構文でも、削除またはアンインストール操作がサポートされます。  
  
  
