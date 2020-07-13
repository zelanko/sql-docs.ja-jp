---
title: トランザクションの管理 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XML for Analysis, transactions
- XMLA, transactions
- explicit transactions [XMLA]
- implicit transactions
- transactions [XML for Analysis]
- rolling back transactions, XMLA
- reference counts [XML for Analysis]
- committing transactions
- starting transactions
ms.assetid: f5112e01-82f8-4870-bfb7-caa00182c999
author: minewiskan
ms.author: owend
ms.openlocfilehash: bff1c60addd25b222905e33bc33e77dd85e88803
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544964"
---
# <a name="managing-transactions-xmla"></a>トランザクションの管理 (XMLA)
  のインスタンスに送信されたすべての XML for Analysis (XMLA) コマンドは [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、現在の暗黙的または明示的なセッションのトランザクションのコンテキスト内で実行されます。 これらの各トランザクションを管理するには、 [BeginTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/begintransaction-element-xmla)、 [committransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/committransaction-element-xmla)、および[RollbackTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/rollbacktransaction-element-xmla)コマンドを使用します。 これらのコマンドを使用して、暗黙の、または明示的なトランザクションの作成や、トランザクション参照カウントの変更、およびトランザクションの開始、コミット、ロールバックを行えます。  
  
## <a name="implicit-and-explicit-transactions"></a>暗黙のトランザクションと明示的なトランザクション  
 トランザクションには、暗黙のものと明示的なものがあります。  
  
 **暗黙のトランザクション**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]コマンドで*implicit* `BeginTransaction` トランザクションの開始が指定されていない場合、XMLA コマンドに対して暗黙のトランザクションを作成します。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は常に、コマンドが成功した場合に暗黙のトランザクションをコミットし、コマンドが失敗した場合に暗黙のトランザクションをロールバックします。  
  
 **明示的なトランザクション**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]コマンドがトランザクションの開始時に*明示的*なトランザクションを作成し `BeginTransaction` ます。 しかし、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、`CommitTransaction` コマンドが送信された場合にのみ明示的なトランザクションをコミットし、`RollbackTransaction` コマンドが送信された場合にのみ明示的なトランザクションをロールバックします。  
  
 また、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、アクティブなトランザクションが完了する前に現在のセッションが終了した場合、暗黙のトランザクションと明示的なトランザクションの両方をロールバックします。  
  
## <a name="transactions-and-reference-counts"></a>トランザクションと参照カウント  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、各セッションに対してトランザクション参照カウントを維持します。 しかし、アクティブなトランザクションは各セッションに対して 1 つだけしか維持されないため、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は入れ子になったトランザクションをサポートしていません。 現在のセッションにアクティブなトランザクションがない場合、トランザクション参照カウントは 0 に設定されます。  
  
 つまり、`BeginTransaction` コマンドごとに参照カウントが 1 つずつ増え、`CommitTransaction` ごとに参照カウントが 1 つずつ減ります。 `CommitTransaction` コマンドによって参照カウントが 0 に設定されると、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] はトランザクションをコミットします。  
  
 ただし、`RollbackTransaction` コマンドは、トランザクション参照カウントの現在の値にかかわりなく、アクティブなトランザクションをロールバックします。 つまり、`RollbackTransaction` コマンドまたは `BeginTransaction` コマンドが送信された数にかかわりなく、`CommitTransaction` コマンドが 1 つあればアクティブなトランザクションがロールバックされ、トランザクション参照カウントは 0 に設定されます。  
  
## <a name="beginning-a-transaction"></a>トランザクションの開始  
 `BeginTransaction` コマンドは、現在のセッションで明示的なトランザクションを開始し、現在のセッションのトランザクション参照カウントを 1 つ増やします。 後続のコマンドはすべて、アクティブなトランザクションをコミットするのに十分な `CommitTransaction` コマンドが送信されるか、1 つの `RollbackTransaction` コマンドが送信されてアクティブなトランザクションがロールバックされるまで、アクティブなトランザクションに含まれるものと見なされます。  
  
## <a name="committing-a-transaction"></a>トランザクションのコミット  
 `CommitTransaction` コマンドは、現在のセッションで `BeginTransaction` コマンドが実行された後に実行されたコマンドの結果をコミットします。 `CommitTransaction` コマンドごとに、セッションのアクティブなトランザクションの参照カウントが 1 つ減ります。 `CommitTransaction` コマンドによって参照カウントが 0 に設定されると、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] はアクティブなトランザクションをコミットします。 アクティブなトランザクションがない場合 (つまり、現在のセッションのトランザクション参照カウントが既に 0 になっている場合)、`CommitTransaction` コマンドを実行するとエラーが発生します。  
  
## <a name="rolling-back-a-transaction"></a>トランザクションのロールバック  
 `RollbackTransaction` コマンドは、現在のセッションで `BeginTransaction` コマンドが実行された後に実行されたコマンドの結果をロールバックします。 `RollbackTransaction` コマンドは、現在のトランザクション参照カウントにかかわりなく、アクティブなトランザクションをロールバックし、トランザクション参照カウントを 0 に設定します。 アクティブなトランザクションがない場合 (つまり、現在のセッションのトランザクション参照カウントが既に 0 になっている場合)、`RollbackTransaction` コマンドを実行するとエラーが発生します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services での XMLA による開発](developing-with-xmla-in-analysis-services.md)  
  
  
