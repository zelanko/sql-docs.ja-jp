---
title: クライアント プロトコル - [名前付きパイプのプロパティ] ダイアログ ボックス ([プロトコル] タブ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- pipes [SQL Server], connecting to
- Named Pipes [SQL Server], default pipe
- client protocols [SQL Server]
ms.assetid: 30fbae62-2f2e-4d36-9c6e-3444fff68781
author: stevestein
ms.author: sstein
ms.openlocfilehash: 169b6d98212c724b8d6c43615ae2fa7eba9cfc7d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85008141"
---
# <a name="client-protocols---named-pipes-properties-protocol-tab"></a>クライアント プロトコル - [名前付きパイプのプロパティ] ダイアログ ボックス ([プロトコル] タブ)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーでは、 **[名前付きパイプのプロパティ]** ダイアログ ボックスの **[プロトコル]** タブを使用して、既定のパイプに関する説明の表示や変更を行います。 別のパイプに接続するには、そのパイプを **[既定のパイプ]** ボックスに入力してください。 接続文字列の詳細については、「 [Creating a Valid Connection String Using Named Pipes](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[既定のパイプ]**  
 名前付きパイプ Net-Library が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の対象インスタンスに接続するために使用する既定のパイプを指定します。 既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は `\\.\pipe\sql\query`  
  
 既定のパイプに接続するには、 `sql\query`  
  
 **有効**  
 可能な値は、 **[はい]** と **[いいえ]** です。  
  
## <a name="see-also"></a>参照  
 [ネットワーク プロトコルの選択](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
