---
title: "sp_cursorunprepare (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_cursorunprepare_TSQL
- sp_cursorunprepare
dev_langs: TSQL
helpviewer_keywords: sp_cursorunprepare
ms.assetid: b46d4813-c4a9-4f9d-9979-2b5082ecf06a
caps.latest.revision: "8"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6a5b0d1bd892119d656d128c20db588a80c904b5
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spcursorunprepare-transact-sql"></a>sp_cursorunprepare (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ストアド プロシージャを sp_cursorprepare で、実行プランが作成された破棄します。 sp_cursorunprepare は、ID を指定して呼び出される、表形式のデータ ストリーム (TDS) パケットで 6 を = です。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_cursorunprepare handle  
```  
  
## <a name="arguments"></a>引数  
 *ハンドル*  
 *処理*ステートメントを準備するときに sp_cursorprepare から返される値。  
  
## <a name="see-also"></a>参照  
 [sp_cursorprepare と #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-cursorprepare-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
