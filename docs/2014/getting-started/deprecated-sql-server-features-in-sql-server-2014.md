---
title: SQL Server 2014 における SQL Server の機能を非推奨 |Microsoft ドキュメント
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fdc0c778-cc8d-42ab-8833-4deb4329f37a
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d0cafd847932ef5f87064defb8e92e7ac4b09784
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164602"
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
 製品の更新プログラム機能は、[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] PCU1 で使用できたスリップストリーム機能に代わるものです。 したがって、スリップストリーム機能に関するコマンド ライン パラメーター /*PCUSource* および /*CUSource*は、使用できなくなりました。 これらのパラメーターは引き続き動作しますが、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] セットアップの将来のリリースでは削除される可能性があります。 /*UpdateSource* パラメーターは、スリップストリームのパラメーター /*PCUSource* および /*CUSource*の機能を結合します。  
  
 使用できたスリップ ストリーム機能の詳細については[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]PCU1 を参照してください[SQL Server 更新プログラムをスリップ ストリーム](http://go.microsoft.com/fwlink/?LinkId=219945)(http://go.microsoft.com/fwlink/?LinkId=219945)です。  
  
## <a name="see-also"></a>参照  
 [旧バージョンとの互換性](../../2014/getting-started/backward-compatibility.md)  
  
  
