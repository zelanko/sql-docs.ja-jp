---
title: "外部結合の実装 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: in-memory-oltp
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67084043-6b23-4975-b9db-6e49923d4bab
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 763ba3a7def8ba4d4ae1f1ff84ed61bfedf6b5ce
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="implementing-an-outer-join"></a>外部結合の実装
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  LEFT OUTER JOIN と RIGHT OUTER JOIN は、 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]以降のネイティブ コンパイル T-SQL モジュールでサポートされています。  
  
  
