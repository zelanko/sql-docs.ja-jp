---
title: PAGE_VERIFY データベース オプションを CHECKSUM に設定 | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 686b9a4a-ea61-4263-9ab8-f444a3077679
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 696d31fbc8c9bf0fd218070228f50311643ec2f9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="set-the-pageverify-database-option-to-checksum"></a>PAGE_VERIFY データベース オプションを CHECKSUM に設定
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このルールでは、PAGE_VERIFY データベース オプションが CHECKSUM に設定されているかどうかを確認します。 PAGE_VERIFY データベース オプションに対して CHECKSUM を有効にすると、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ではページをディスクに書き込む際に、ページ全体の内容のチェックサムを計算し、ページ ヘッダーに計算したチェックサムの値を格納します。 このページがディスクから読み取られるときに、チェックサムが再計算され、ページ ヘッダーに格納されているチェックサムの値と比較されます。 これにより、高レベルなデータ ファイル整合性が提供されます。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 PAGE_VERIFY データベース オプションを CHECKSUM に設定します。  
  
## <a name="for-more-information"></a>詳細情報  
 [ALTER DATABASE SET オプション &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
  
