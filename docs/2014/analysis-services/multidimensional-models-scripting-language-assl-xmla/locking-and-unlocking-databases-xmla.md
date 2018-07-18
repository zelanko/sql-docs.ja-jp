---
title: ロックとデータベース (XMLA) をロック解除 |Microsoft Docs
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
- locking [XML for Analysis]
- XML for Analysis, locking
- XMLA, locking
- unlocking objects
ms.assetid: 451afa58-ce03-4ecc-8dd3-9e7e8559b5f1
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fa6eab7a4d0ebe15e87ee83b60020b7a1f809ae8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37278360"
---
# <a name="locking-and-unlocking-databases-xmla"></a>データベースのロックおよびロック解除 (XMLA)
  ロックして、それぞれを使用してデータベースをロック解除することができます、[ロック](../xmla/xml-elements-commands/lock-element-xmla.md)と[Unlock](../xmla/xml-elements-commands/unlock-element-xmla.md) xml for Analysis (XMLA) コマンド。 通常、他の XMLA コマンドは、実行時にコマンドを完了させる必要に応じて、自動的にオブジェクトをロック/ロック解除します。 明示的にロックまたはなど、単一のトランザクション内で複数のコマンドを実行するデータベースのロックを解除することができます、[バッチ](../xmla/xml-elements-commands/batch-element-xmla.md)コマンドから、他のアプリケーション データベースへの書き込みトランザクションをコミットするを防止します。  
  
## <a name="locking-databases"></a>データベースのロック  
 `Lock` コマンドは、現在アクティブなトランザクションのコンテキスト内で、共有オブジェクトまたは排他的に使用されるオブジェクトをロックします。 オブジェクトをロックすると、そのロックが解除されるまでトランザクションはコミットできません。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 2 種類の共有ロックと排他ロックをサポートしています。 サポートされているロックの種類の詳細については[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]を参照してください[Mode 要素&#40;XMLA&#41;](../xmla/xml-elements-properties/mode-element-xmla.md)します。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、データベースに対するロックだけが可能です。 [オブジェクト](../xmla/xml-elements-properties/object-element-xmla.md)要素へのオブジェクト参照を含める必要があります、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース。 `Object` 要素が指定されていない場合、またはデータベース以外のオブジェクトを `Object` 要素が参照している場合には、エラーが発生します。  
  
> [!IMPORTANT]  
>  `Lock` コマンドを明示的に発行できるのは、データベース管理者またはサーバー管理者だけです。  
  
 他のコマンドは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに対する `Lock` コマンドを暗黙的に発行します。 いずれかなど、データベースからデータまたはメタデータを読み取る操作[Discover](../xmla/xml-elements-methods-discover.md)メソッドまたは[Execute](../xmla/xml-elements-methods-execute.md)メソッドを実行している、[ステートメント](../xmla/xml-elements-commands/statement-element-xmla.md)コマンドで、共有を暗黙的に発行データベースをロックします。 オブジェクトへのデータまたはメタデータの変更をコミットするトランザクションを[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]などのデータベース、`Execute`メソッドを実行している、 [Alter](../xmla/xml-elements-commands/alter-element-xmla.md)コマンドで、データベースに対する排他ロックを暗黙的に発行します。  
  
## <a name="unlocking-objects"></a>データベースのロック解除  
 `Unlock` コマンドは、現在アクティブなトランザクションのコンテキスト内で確立されたロックを解除します。  
  
> [!IMPORTANT]  
>  データベース管理者またはサーバー管理者のみに明示的に発行できる、`Unlock`コマンド。  
  
 すべてのロックは、現在のトランザクションのコンテキスト内で保持されます。 現在のトランザクションがコミットまたはロールバックされると、そのトランザクション内で定義されたすべてのロックは自動的に解放されます。  
  
## <a name="see-also"></a>参照  
 [要素をロック&#40;XMLA&#41;](../xmla/xml-elements-commands/lock-element-xmla.md)   
 [要素のロック解除&#40;XMLA&#41;](../xmla/xml-elements-commands/unlock-element-xmla.md)   
 [Analysis Services での XMLA による開発](developing-with-xmla-in-analysis-services.md)  
  
  
