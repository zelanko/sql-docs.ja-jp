---
title: "最適なパフォーマンスを実現するための max degree of parallelism オプションの設定 | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Best Practices [Database Engine]
ms.assetid: ec908006-67ae-4674-9a61-25ea741d6197
caps.latest.revision: "11"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6efd8d390f0f468b8e4236190e58d52acc043a62
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="set-the-max-degree-of-parallelism-option-for-optimal-performance"></a>最適なパフォーマンスを実現するための max degree of parallelism オプションの設定
  このルールでは、値の max degree of parallelism (MAXDOP) オプションが 8 より大きいかどうかを確認します。 このオプションを大きな値に設定すると、多くの場合、不要なリソース消費やパフォーマンスの低下が発生します。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 sp_configure を使用して max degree of parallelism オプションを 8 以下に設定してください。  
  
## <a name="for-more-information"></a>詳細情報  
 [サポート技術情報の資料 329204](http://go.microsoft.com/fwlink/?linkid=117786)  
  
 [max degree of parallelism サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)  
  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
