---
title: トランザクションの管理 (XMLA) |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6c85b1f9db4667c64bed7cf87189e48b507e5f75
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63055077"
---
# <a name="managing-transactions-xmla"></a>トランザクションの管理 (XMLA)
  すべての XML for Analysis (XMLA) コマンドがのインスタンスに送信される[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]現在暗黙的または明示的なセッションで、トランザクションのコンテキスト内で実行します。 使用するこれらの各トランザクションを管理する、 [BeginTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/begintransaction-element-xmla)、 [CommitTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/committransaction-element-xmla)、および[RollbackTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/rollbacktransaction-element-xmla)コマンド。 これらのコマンドを使用して、暗黙の、または明示的なトランザクションの作成や、トランザクション参照カウントの変更、およびトランザクションの開始、コミット、ロールバックを行えます。  
  
## <a name="implicit-and-explicit-transactions"></a>暗黙のトランザクションと明示的なトランザクション  
 トランザクションには、暗黙のものと明示的なものがあります。  
  
 **暗黙のトランザクション**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 作成、*暗黙的な*のトランザクションを XMLA コマンドの場合、 **BeginTransaction**コマンドがトランザクションの開始を指定していません。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は常に、コマンドが成功した場合に暗黙のトランザクションをコミットし、コマンドが失敗した場合に暗黙のトランザクションをロールバックします。  
  
 **明示的なトランザクション**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 作成、*明示的な*トランザクション場合、 **BeginTransaction**コマンドは、トランザクションの開始。 ただし、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]場合のみ、明示的なトランザクションをコミットを**CommitTransaction**コマンドを送信して場合、明示的なトランザクションをロールバック、 **RollbackTransaction**コマンドを送信します。  
  
 また、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、アクティブなトランザクションが完了する前に現在のセッションが終了した場合、暗黙のトランザクションと明示的なトランザクションの両方をロールバックします。  
  
## <a name="transactions-and-reference-counts"></a>トランザクションと参照カウント  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、各セッションに対してトランザクション参照カウントを維持します。 しかし、アクティブなトランザクションは各セッションに対して 1 つだけしか維持されないため、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は入れ子になったトランザクションをサポートしていません。 現在のセッションにアクティブなトランザクションがない場合、トランザクション参照カウントは 0 に設定されます。  
  
 つまり、各**BeginTransaction**コマンドは、1 つずつ、それぞれの中に参照カウントをインクリメント**CommitTransaction**参照カウントを 1 つのコマンドをデクリメントします。 場合、 **CommitTransaction**コマンドでは、トランザクション数を 0 に設定[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]トランザクションをコミットします。  
  
 ただし、 **RollbackTransaction**コマンドが、トランザクション参照カウントの現在の値に関係なく、アクティブなトランザクションをロールバックします。 つまり、1 つ**RollbackTransaction**コマンド数に関係なく、アクティブなトランザクションがロールバック**BeginTransaction**コマンドまたは**CommitTransaction**コマンドは、送信され、トランザクション参照カウントを 0 に設定します。  
  
## <a name="beginning-a-transaction"></a>トランザクションを開始します。  
 **BeginTransaction**コマンドは、現在のセッションで明示的なトランザクションを開始し、いずれかによって、現在のセッション、トランザクション参照カウントをインクリメントします。 すべての後続のコマンドはいずれかまで、アクティブなトランザクション内で十分であると見なされます**CommitTransaction**コマンドは、1 つ、アクティブなトランザクションのコミットに送信**RollbackTransaction**、アクティブなトランザクションをロールバックするコマンドを送信します。  
  
## <a name="committing-a-transaction"></a>トランザクションをコミットします。  
 **CommitTransaction**コマンドがコミット後に実行されたコマンドの結果、 **BeginTransaction**コマンドが現在のセッションで実行されました。 各**CommitTransaction**セッションでアクティブなトランザクションの参照カウントをデクリメントをコマンドします。 場合、 **CommitTransaction**コマンドでは、参照カウントを 0 に設定[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]アクティブなトランザクションをコミットします。 アクティブなトランザクションが存在しない場合 (つまり、現在のセッションのトランザクション参照カウントは既にゼロに設定)、 **CommitTransaction**コマンド エラーが発生します。  
  
## <a name="rolling-back-a-transaction"></a>トランザクションのロールバック  
 **RollbackTransaction**コマンドはロールバック後に実行されたコマンドの結果、 **BeginTransaction**コマンドが現在のセッションで実行されました。 **RollbackTransaction**コマンドは、現在のトランザクション参照カウントに関係なく、アクティブなトランザクションをロールバックし、トランザクション参照カウントを 0 に設定します。 アクティブなトランザクションが存在しない場合 (つまり、現在のセッションのトランザクション参照カウントは既にゼロに設定)、 **RollbackTransaction**コマンド エラーが発生します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services での XMLA による開発](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
