---
title: SQL フルテキスト フィルター デーモン ランチャー (SQL Server 構成マネージャー) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: d0dc03db-5f76-4558-b041-1ac7b9b5bb16
author: stevestein
ms.author: sstein
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: b48a0fe57fead6fdcf90e261d0a8aeff571e6cdd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47676154"
---
# <a name="sql-full-text-filter-daemon-launcher-sql-server-configuration-manager"></a>SQL フルテキスト フィルター デーモン ランチャー (SQL Server 構成マネージャー)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]以降では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フルテキスト検索でフィルター処理や単語区切りを行うフィルター デーモン ホスト プロセスを開始するために、SQL フルテキスト フィルター デーモン ランチャー (FDHOST ランチャー) サービスが使用されます。 フルテキスト検索を使用するには、このサービスが実行されている必要があります。 FDHOST ランチャー サービスは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の特定のインスタンスに関連付けられているインスタンス対応のサービスです。 FDHOST ランチャー サービスにより、開始された各フィルター デーモン ホスト プロセスにサービス アカウント情報が反映されます。 フィルター デーモン ホスト プロセスの詳細については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「フルテキスト検索のアーキテクチャ」を参照してください。  
  
  
