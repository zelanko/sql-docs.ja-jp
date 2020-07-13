---
title: データベース エンジン拡張ストアド プロシージャ プログラミング | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], programming
- stored procedures [SQL Server], extended
- Database Engine [SQL Server], stored procedures
- macros [SQL Server]
- Extended Stored Procedure API [SQL Server]
ms.assetid: 158a6765-0542-4e84-b5ab-f173d946ef5e
author: rothja
ms.author: jroth
ms.openlocfilehash: fecb8f996ddfcaede83cdb330e9c82bffdce5819
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84953036"
---
# <a name="database-engine-extended-stored-procedure-programming"></a>データベース エンジン拡張ストアド プロシージャ プログラミング
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../includes/ssnotedepfuturedontuse-md.md)] 代わりに CLR Integration を使用してください。 詳細については、「[共通言語ランタイム &#40;CLR&#41; 統合のプログラミング概念](clr-integration/common-language-runtime-clr-integration-programming-concepts.md)」をご覧ください。  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)]拡張ストアドプロシージャ api には、機能を拡張するためのサーバーベースのアプリケーションプログラミングインターフェイス (api) が用意されて [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] います。 この API は、拡張ストアド プロシージャおよびゲートウェイ アプリケーションのカテゴリでアプリケーションの構築に使用する C および C++ の関数とマクロで構成されています。  
  
 拡張ストアド プロシージャを使用すると、C などのプログラミング言語を使用してユーザー独自の外部ルーチンを作成できます。拡張ストアド プロシージャは、ユーザーには通常のストアド プロシージャのように見え、同じように実行されます。 拡張ストアド プロシージャにはパラメーターを渡すことができ、拡張ストアド プロシージャは結果や状態を返すことができます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [拡張ストアド プロシージャのプログラミング](extended-stored-procedures-programming/database-engine-extended-stored-procedures-programming.md)  
 拡張ストアド プロシージャを作成、管理、および使用する方法について説明します。  
  
 [拡張ストアド プロシージャのプログラマーズ リファレンス](extended-stored-procedures-reference/database-engine-extended-stored-procedures-reference.md)  
 拡張ストアド プロシージャ API に関する参照トピックが記載されています。  
  
  
