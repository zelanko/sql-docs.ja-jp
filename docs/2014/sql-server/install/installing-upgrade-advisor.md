---
title: アップグレードアドバイザーをインストールしています |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- Setup [Upgrade Advisor]
- Upgrade Advisor [SQL Server], installing
ms.assetid: 1b7d6eca-1df1-47df-bbba-0fc485706a95
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 40f214b01f3e2066708a060c5f3ad1e8aa4a0a23
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065340"
---
# <a name="installing-upgrade-advisor"></a>アップグレード アドバイザーのインストール
  SQL Server 2014 Upgrade Advisor のインストール場所は、分析する内容によって異なります。 アップグレード アドバイザーでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のすべての [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンポーネントをリモートで分析できます。 のインスタンスをスキャンしない場合は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に接続できる任意のコンピューターにアップグレードアドバイザーをインストールでき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。また、[アップグレードアドバイザーの前提条件](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)を満たしている必要があります。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインスタンスをスキャンする場合は、アップグレード アドバイザーをレポート サーバーにインストールする必要があります。  
  
 **SQLUA.msi**ファイルを実行して、アップグレードアドバイザーをインストールします。 コマンド プロンプトからインストールすると、自動インストールを実行できます。 構文と例について[は、「コマンドプロンプトからのアップグレードアドバイザーのインストール](../../../2014/sql-server/install/installing-upgrade-advisor-from-the-command-prompt.md)」を参照してください。  
  
 SQLUA.msi の入手先:  
  
-   製品メディアの**redist**フォルダー内 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
-   [SQL 2014 Feature Pack のダウンロード](https://www.microsoft.com/download/details.aspx?id=42295)の一部として。  
  
## <a name="uninstalling-upgrade-advisor"></a>アップグレード アドバイザーのアンインストール  
 アップグレードアドバイザーをアンインストールするには、[**プログラムの追加と削除**] を使用します。 コマンド プロンプトの構文でも、削除またはアンインストール操作がサポートされます。  
  
  
