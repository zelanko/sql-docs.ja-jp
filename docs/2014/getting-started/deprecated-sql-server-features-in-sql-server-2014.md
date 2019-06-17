---
title: SQL Server 2014 における SQL Server の機能を非推奨とされます |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: fdc0c778-cc8d-42ab-8833-4deb4329f37a
author: mightypen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5d28d829280e205028a99afd9fec2e019bf567ab
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66089479"
---
# <a name="deprecated-sql-server-features-in-sql-server-2014"></a>SQL Server 2014 の非推奨の SQL Server 機能
  このトピックでは、[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] でまだ使用できるものの、非推奨となった機能について説明します。 これらの機能は [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の今後のリリースで削除される予定です。 非推奨の機能を新しいアプリケーションで使用しないでください。  
  
## <a name="features-not-supported-in-the-next-version-of-includessnoversionincludesssnoversion-mdmd"></a>[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の次のバージョンでサポートされない機能  
 以下の [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] 機能は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の次のバージョンではサポートされません。 新規の開発作業ではこれらの機能を使用しないようにし、現在これらの機能を使用しているアプリケーションはできるだけ早く修正してください。 機能名の列は、トレース イベントには ObjectName として表示され、パフォーマンス カウンターおよび sys.dm_os_performance_counters には instance_name として表示されます。 機能 ID は ObjectId としてトレース イベントに表示されます。  
  
|カテゴリ|非推奨の機能|代替|機能名|機能 ID|  
|--------------|------------------------|-----------------|------------------|----------------|  
|データ プログラミング|[sys.soap_endpoints &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-soap-endpoints-transact-sql)|Windows Communications Foundation (WCF) または ASP.NET|ネイティブ XML Web サービス|22|  
|データ プログラミング|[sys.endpoint_webmethods &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-endpoint-webmethods-transact-sql)|Windows Communications Foundation (WCF) または ASP.NET|ネイティブ XML Web サービス|23|  
  
### <a name="slipstream-functionality"></a>スリップストリーム機能  
 製品の更新プログラム機能は、 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] PCU1 で使用できたスリップストリーム機能に代わるものです。 したがって、スリップストリーム機能に関するコマンド ライン パラメーター /*PCUSource* および /*CUSource*は、使用できなくなりました。 これらのパラメーターは引き続き動作しますが、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] セットアップの将来のリリースでは削除される可能性があります。 /*UpdateSource* パラメーターは、スリップストリームのパラメーター /*PCUSource* および /*CUSource*の機能を結合します。  
  
 使用できたスリップ ストリーム機能の詳細については[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]PCU1 を参照してください[SQL Server 更新プログラムをスリップ ストリーム](https://go.microsoft.com/fwlink/?LinkId=219945)(https://go.microsoft.com/fwlink/?LinkId=219945) します。  
  
## <a name="see-also"></a>参照  
 [旧バージョンとの互換性](../../2014/getting-started/backward-compatibility.md)  
  
  
