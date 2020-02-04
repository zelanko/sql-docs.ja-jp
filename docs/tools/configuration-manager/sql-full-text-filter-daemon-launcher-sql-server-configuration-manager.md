---
title: SQL フルテキスト フィルター デーモン ランチャー (SQL Server 構成マネージャー)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: d0dc03db-5f76-4558-b041-1ac7b9b5bb16
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: bf40f8c38e7e674a3930e09819af973cb63fd5c3
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75306713"
---
# <a name="sql-full-text-filter-daemon-launcher-sql-server-configuration-manager"></a>SQL フルテキスト フィルター デーモン ランチャー (SQL Server 構成マネージャー)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]以降では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フルテキスト検索でフィルター処理や単語区切りを行うフィルター デーモン ホスト プロセスを開始するために、SQL フルテキスト フィルター デーモン ランチャー (FDHOST ランチャー) サービスが使用されます。 フルテキスト検索を使用するには、このサービスが実行されている必要があります。 FDHOST ランチャー サービスは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の特定のインスタンスに関連付けられているインスタンス対応のサービスです。 FDHOST ランチャー サービスにより、開始された各フィルター デーモン ホスト プロセスにサービス アカウント情報が反映されます。 フィルター デーモン ホスト プロセスの詳細については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「フルテキスト検索のアーキテクチャ」を参照してください。  
  
  
