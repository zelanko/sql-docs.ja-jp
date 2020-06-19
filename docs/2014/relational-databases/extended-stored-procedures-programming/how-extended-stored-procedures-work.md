---
title: 拡張ストアドプロシージャのしくみ |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], about extended stored procedures
ms.assetid: 6e946d8c-3268-4b59-8a1c-1637909cd701
author: rothja
ms.author: jroth
ms.openlocfilehash: 75082fed6b70c214b4f55b85034ffa371824d24f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85027130"
---
# <a name="how-extended-stored-procedures-work"></a>拡張ストアド プロシージャのしくみ
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 代わりに CLR Integration を使用してください。  
  
 拡張ストアド プロシージャが動作するプロセスは次のとおりです。  
  
1.  クライアントが拡張ストアドプロシージャを実行すると、要求はクライアントアプリケーションからに表形式のデータストリーム (TDS) 形式または Simple Object Access Protocol (SOAP) 形式で送信され [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は拡張ストアド プロシージャに関連付けられた DLL を検索し、対象の DLL がまだロードされていない場合はロードします。  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、要求されている拡張ストアド プロシージャ (DLL 内に関数として実装されている) を呼び出します。  
  
4.  拡張ストアド プロシージャは拡張ストアド プロシージャ API を介してサーバーに結果セットを渡し、パラメーターを返します。  
  
## <a name="see-also"></a>参照  
 [データベース エンジン拡張ストアド プロシージャ プログラミング](../database-engine-extended-stored-procedure-programming.md)  
  
  
