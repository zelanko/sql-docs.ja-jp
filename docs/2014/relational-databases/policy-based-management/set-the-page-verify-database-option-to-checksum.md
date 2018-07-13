---
title: PAGE_VERIFY データベース オプションを CHECKSUM に設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 686b9a4a-ea61-4263-9ab8-f444a3077679
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e38fede037b29e1048234d82a7fabaa725a32095
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37221372"
---
# <a name="set-the-pageverify-database-option-to-checksum"></a>PAGE_VERIFY データベース オプションを CHECKSUM に設定
  このルールでは、PAGE_VERIFY データベース オプションが CHECKSUM に設定されているかどうかを確認します。 PAGE_VERIFY データベース オプションに対して CHECKSUM を有効にすると、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ではページをディスクに書き込む際に、ページ全体の内容のチェックサムを計算し、ページ ヘッダーに計算したチェックサムの値を格納します。 このページがディスクから読み取られるときに、チェックサムが再計算され、ページ ヘッダーに格納されているチェックサムの値と比較されます。 これにより、高レベルなデータ ファイル整合性が提供されます。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 PAGE_VERIFY データベース オプションを CHECKSUM に設定します。  
  
## <a name="for-more-information"></a>詳細情報  
 [ALTER DATABASE SET オプション &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
  
