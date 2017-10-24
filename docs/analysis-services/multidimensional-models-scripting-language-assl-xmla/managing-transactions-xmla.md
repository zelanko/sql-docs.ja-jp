---
title: "トランザクション (XMLA) の管理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
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
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6b5e9a8976614439ebfabc736052e7458d4e8aa9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="managing-transactions-xmla"></a>トランザクションの管理 (XMLA)
  すべての XML for Analysis (XMLA) コマンドがのインスタンスに送信される[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]現在暗黙的または明示的なセッションで、トランザクションのコンテキスト内で実行します。 使用するこれらの各トランザクションを管理するため、 [BeginTransaction](../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)、 [CommitTransaction](../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)、および[RollbackTransaction](../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)コマンド。 これらのコマンドを使用して、暗黙の、または明示的なトランザクションの作成や、トランザクション参照カウントの変更、およびトランザクションの開始、コミット、ロールバックを行えます。  
  
## <a name="implicit-and-explicit-transactions"></a>暗黙のトランザクションと明示的なトランザクション  
 トランザクションには、暗黙のものと明示的なものがあります。  
  
 **暗黙のトランザクション**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]作成、*暗黙的な*のトランザクションを XMLA コマンドが、 **BeginTransaction**コマンドでは、トランザクションの開始が指定されていません。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は常に、コマンドが成功した場合に暗黙のトランザクションをコミットし、コマンドが失敗した場合に暗黙のトランザクションをロールバックします。  
  
 **明示的なトランザクション**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]作成、*明示的な*トランザクション場合、 **BeginTransaction**トランザクションのコマンドを開始します。 ただし、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]場合にのみ明示的なトランザクションをコミット、 **CommitTransaction**コマンドが送信され、場合は、明示的なトランザクションをロールバック、 **RollbackTransaction**コマンドを送信します。  
  
 また、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、アクティブなトランザクションが完了する前に現在のセッションが終了した場合、暗黙のトランザクションと明示的なトランザクションの両方をロールバックします。  
  
## <a name="transactions-and-reference-counts"></a>トランザクションと参照カウント  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、各セッションに対してトランザクション参照カウントを維持します。 しかし、アクティブなトランザクションは各セッションに対して 1 つだけしか維持されないため、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は入れ子になったトランザクションをサポートしていません。 現在のセッションにアクティブなトランザクションがない場合、トランザクション参照カウントは 0 に設定されます。  
  
 つまり、各**BeginTransaction**コマンドは、いずれかによって、それぞれの中に参照カウントをインクリメント**CommitTransaction**参照カウントが 1 つのコマンドをデクリメントします。 場合、 **CommitTransaction**コマンドでは、トランザクション カウントを設定には、0[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]トランザクションをコミットします。  
  
 ただし、 **RollbackTransaction**コマンドは、トランザクション参照カウントの現在の値に関係なく、アクティブなトランザクションをロールバックします。 つまり、1 つ**RollbackTransaction**コマンド数に関係なく、アクティブなトランザクションがロールバック**BeginTransaction**コマンドまたは**CommitTransaction**コマンドは、送信され、トランザクション参照カウントを 0 に設定します。  
  
## <a name="beginning-a-transaction"></a>トランザクションを開始します。  
 **BeginTransaction**コマンドは、現在のセッションで明示的なトランザクションを開始し、いずれかによって、現在のセッションのトランザクション参照カウントをインクリメントします。 すべての後続のコマンドはいずれかされるまで、アクティブなトランザクション内で十分であると見なされます**CommitTransaction**コマンドが 1 つのアクティブなトランザクションのコミットに送信**RollbackTransaction**、アクティブなトランザクションをロールバックするコマンドを送信します。  
  
## <a name="committing-a-transaction"></a>トランザクションをコミットします。  
 **CommitTransaction**コマンドがコミット後に実行されたコマンドの結果、 **BeginTransaction**コマンドは、現在のセッションで実行されています。 各**CommitTransaction**セッションでアクティブなトランザクションの参照カウントをデクリメントをコマンドします。 場合、 **CommitTransaction**コマンドには、0、参照カウントを設定する[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]アクティブなトランザクションをコミットします。 アクティブなトランザクションが存在しない場合 (つまり、現在のセッションのトランザクション参照カウントは既に 0 に設定)、 **CommitTransaction**コマンドをエラーが発生します。  
  
## <a name="rolling-back-a-transaction"></a>トランザクションのロールバック  
 **RollbackTransaction**コマンドの後に実行されたコマンドの結果をロールバック、 **BeginTransaction**コマンドは、現在のセッションで実行されています。 **RollbackTransaction**コマンドは、現在のトランザクション参照カウントに関係なく、アクティブなトランザクションをロールバックし、トランザクション参照カウントを 0 に設定します。 アクティブなトランザクションが存在しない場合 (つまり、現在のセッションのトランザクション参照カウントは既に 0 に設定)、 **RollbackTransaction**コマンドをエラーが発生します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services の XMLA による開発](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  

