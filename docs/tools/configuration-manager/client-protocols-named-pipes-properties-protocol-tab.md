---
title: "クライアント プロトコル - 名前付きパイプのプロパティ (プロトコル タブ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipes [SQL Server], connecting to
- Named Pipes [SQL Server], default pipe
- client protocols [SQL Server]
ms.assetid: 30fbae62-2f2e-4d36-9c6e-3444fff68781
caps.latest.revision: "23"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a6f971e2daaf14ae55df79a88650777c4f0e421c
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="client-protocols---named-pipes-properties-protocol-tab"></a>クライアント プロトコル - [名前付きパイプのプロパティ] ダイアログ ボックス ([プロトコル] タブ)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーでは、 **[名前付きパイプのプロパティ]** ダイアログ ボックスの **[プロトコル]** タブを使用して、既定のパイプに関する説明の表示や変更を行います。 別のパイプに接続するには、そのパイプを **[既定のパイプ]** ボックスに入力してください。 接続文字列の詳細については、「 [Creating a Valid Connection String Using Named Pipes](http://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[既定のパイプ]**  
 名前付きパイプ Net-Library が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の対象インスタンスに接続するために使用する既定のパイプを指定します。 既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は `\\.\pipe\sql\query`  
  
 既定のパイプに接続するには、 `sql\query`  
  
 **有効**  
 指定できる値は **[はい]** か **[いいえ]**のいずれかです。  
  
## <a name="see-also"></a>参照  
 [ネットワーク プロトコルの選択](http://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)  
  
  
