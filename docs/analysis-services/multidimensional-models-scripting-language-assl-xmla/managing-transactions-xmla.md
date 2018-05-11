---
title: トランザクション (XMLA) の管理 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f61007d4a9ebed2eb3baf3a8453276d7d3e42af8
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="managing-transactions-xmla"></a>トランザクションの管理 (XMLA)
  すべての XML for Analysis (XMLA) コマンドがのインスタンスに送信される[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]現在暗黙的または明示的なセッションで、トランザクションのコンテキスト内で実行します。 使用するこれらの各トランザクションを管理するため、 [BeginTransaction](../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)、 [CommitTransaction](../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)、および[RollbackTransaction](../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)コマンド。 これらのコマンドを使用して、暗黙の、または明示的なトランザクションの作成や、トランザクション参照カウントの変更、およびトランザクションの開始、コミット、ロールバックを行えます。  
  
## <a name="implicit-and-explicit-transactions"></a>暗黙のトランザクションと明示的なトランザクション  
 トランザクションには、暗黙のものと明示的なものがあります。  
  
 **暗黙のトランザクション**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 作成、*暗黙的な*のトランザクションを XMLA コマンドが、 **BeginTransaction**コマンドでは、トランザクションの開始が指定されていません。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は常に、コマンドが成功した場合に暗黙のトランザクションをコミットし、コマンドが失敗した場合に暗黙のトランザクションをロールバックします。  
  
 **明示的なトランザクション**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 作成、*明示的な*トランザクション場合、 **BeginTransaction**トランザクションのコマンドを開始します。 ただし、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]場合にのみ明示的なトランザクションをコミット、 **CommitTransaction**コマンドが送信され、場合は、明示的なトランザクションをロールバック、 **RollbackTransaction**コマンドを送信します。  
  
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
  
  
