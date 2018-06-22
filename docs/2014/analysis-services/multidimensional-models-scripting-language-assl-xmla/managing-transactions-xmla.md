---
title: トランザクション (XMLA) の管理 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 84ec16569d7e4118c159b7a611cba9d711b9d761
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070585"
---
# <a name="managing-transactions-xmla"></a>トランザクションの管理 (XMLA)
  すべての XML for Analysis (XMLA) コマンドがのインスタンスに送信される[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]現在暗黙的または明示的なセッションで、トランザクションのコンテキスト内で実行します。 使用するこれらの各トランザクションを管理するため、 [BeginTransaction](../xmla/xml-elements-commands/begintransaction-element-xmla.md)、 [CommitTransaction](../xmla/xml-elements-commands/committransaction-element-xmla.md)、および[RollbackTransaction](../xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)コマンド。 これらのコマンドを使用して、暗黙の、または明示的なトランザクションの作成や、トランザクション参照カウントの変更、およびトランザクションの開始、コミット、ロールバックを行えます。  
  
## <a name="implicit-and-explicit-transactions"></a>暗黙のトランザクションと明示的なトランザクション  
 トランザクションには、暗黙のものと明示的なものがあります。  
  
 **暗黙のトランザクション**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 作成、*暗黙的な*のトランザクションを XMLA コマンドが、`BeginTransaction`コマンドでは、トランザクションの開始が指定されていません。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は常に、コマンドが成功した場合に暗黙のトランザクションをコミットし、コマンドが失敗した場合に暗黙のトランザクションをロールバックします。  
  
 **明示的なトランザクション**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 作成、*明示的な*トランザクション場合、`BeginTransaction`トランザクションのコマンドを開始します。 しかし、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、`CommitTransaction` コマンドが送信された場合にのみ明示的なトランザクションをコミットし、`RollbackTransaction` コマンドが送信された場合にのみ明示的なトランザクションをロールバックします。  
  
 また、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、アクティブなトランザクションが完了する前に現在のセッションが終了した場合、暗黙のトランザクションと明示的なトランザクションの両方をロールバックします。  
  
## <a name="transactions-and-reference-counts"></a>トランザクションと参照カウント  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、各セッションに対してトランザクション参照カウントを維持します。 しかし、アクティブなトランザクションは各セッションに対して 1 つだけしか維持されないため、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は入れ子になったトランザクションをサポートしていません。 現在のセッションにアクティブなトランザクションがない場合、トランザクション参照カウントは 0 に設定されます。  
  
 つまり、`BeginTransaction` コマンドごとに参照カウントが 1 つずつ増え、`CommitTransaction` ごとに参照カウントが 1 つずつ減ります。 `CommitTransaction` コマンドによって参照カウントが 0 に設定されると、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] はトランザクションをコミットします。  
  
 ただし、`RollbackTransaction` コマンドは、トランザクション参照カウントの現在の値にかかわりなく、アクティブなトランザクションをロールバックします。 つまり、`RollbackTransaction` コマンドまたは `BeginTransaction` コマンドが送信された数にかかわりなく、`CommitTransaction` コマンドが 1 つあればアクティブなトランザクションがロールバックされ、トランザクション参照カウントは 0 に設定されます。  
  
## <a name="beginning-a-transaction"></a>トランザクションを開始します。  
 `BeginTransaction` コマンドは、現在のセッションで明示的なトランザクションを開始し、現在のセッションのトランザクション参照カウントを 1 つ増やします。 後続のコマンドはすべて、アクティブなトランザクションをコミットするのに十分な `CommitTransaction` コマンドが送信されるか、1 つの `RollbackTransaction` コマンドが送信されてアクティブなトランザクションがロールバックされるまで、アクティブなトランザクションに含まれるものと見なされます。  
  
## <a name="committing-a-transaction"></a>トランザクションをコミットします。  
 `CommitTransaction` コマンドは、現在のセッションで `BeginTransaction` コマンドが実行された後に実行されたコマンドの結果をコミットします。 `CommitTransaction` コマンドごとに、セッションのアクティブなトランザクションの参照カウントが 1 つ減ります。 `CommitTransaction` コマンドによって参照カウントが 0 に設定されると、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] はアクティブなトランザクションをコミットします。 アクティブなトランザクションがない場合 (つまり、現在のセッションのトランザクション参照カウントが既に 0 になっている場合)、`CommitTransaction` コマンドを実行するとエラーが発生します。  
  
## <a name="rolling-back-a-transaction"></a>トランザクションのロールバック  
 `RollbackTransaction` コマンドは、現在のセッションで `BeginTransaction` コマンドが実行された後に実行されたコマンドの結果をロールバックします。 `RollbackTransaction` コマンドは、現在のトランザクション参照カウントにかかわりなく、アクティブなトランザクションをロールバックし、トランザクション参照カウントを 0 に設定します。 アクティブなトランザクションがない場合 (つまり、現在のセッションのトランザクション参照カウントが既に 0 になっている場合)、`RollbackTransaction` コマンドを実行するとエラーが発生します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services での XMLA による開発](developing-with-xmla-in-analysis-services.md)  
  
  