---
title: 拡張ストアド プロシージャのしくみ |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], about extended stored procedures
ms.assetid: 6e946d8c-3268-4b59-8a1c-1637909cd701
author: rothja
ms.author: jroth
ms.openlocfilehash: 3c9b8bf0da73545a9ec9c582aedf5b8f44980c5c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68064329"
---
# <a name="how-extended-stored-procedures-work"></a>拡張ストアド プロシージャのしくみ

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 代わりに CLR Integration を使用してください。  
  
 拡張ストアド プロシージャが動作するプロセスは次のとおりです。  
  
1.  表形式データ ストリーム (TDS) または、クライアント アプリケーションからの簡易オブジェクト アクセス プロトコル (SOAP) 形式で要求を送信するクライアントは、拡張ストアド プロシージャを実行するとき[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は拡張ストアド プロシージャに関連付けられた DLL を検索し、対象の DLL がまだロードされていない場合はロードします。  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、要求されている拡張ストアド プロシージャ (DLL 内に関数として実装されている) を呼び出します。  
  
4.  拡張ストアド プロシージャは拡張ストアド プロシージャ API を介してサーバーに結果セットを渡し、パラメーターを返します。  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

