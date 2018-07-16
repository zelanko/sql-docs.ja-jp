---
title: チェック アウトの管理 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- source controls [SQL Server Management Studio], checkouts
- checkouts [SQL Server Management Studio]
- checking out files
ms.assetid: ddd4adba-d432-4005-9cb2-bb9ee3163d8e
caps.latest.revision: 20
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a64e2346479c95327c3f183331cc7971481521b1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37320712"
---
# <a name="manage-checkouts"></a>チェック アウトを管理します。
  ソース管理にファイルを追加した後にそのファイルを変更するには、まずファイルをチェックアウトする必要があります。 ソース管理からファイルをチェックアウトすると、ソース管理プロバイダーによって、最新バージョンのコピーがローカル ディスクに作成され、ファイルの読み取り専用属性が解除されます。 状況によっては、ファイルをチェックアウトしないで編集することが必要になる場合もあります。 ファイルをチェック アウトしないで編集の詳細については、次を参照してください。[チェックインされたファイルの編集](../../2014/database-engine/edit-checked-in-files.md)します。  
  
 使用することができます[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]ファイルを手動または自動的にチェック アウトします。 ファイルをチェック アウト手動でのファイルを含むソリューションを開くことで、[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]環境では、クリックして、**チェック アウト**コマンド。 ファイルを自動的にチェックアウトするには、[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 環境でそのための設定を行う必要があります。  
  
 管理者がソース管理プロバイダーに対して設定したオプションによっては、ファイルのチェックアウトを排他モードで行うことも、共有モードで行うこともできます。 ファイルを排他モードでチェックアウトする場合は、チェックアウトしたユーザーだけがそのファイルを変更できます。このユーザーがファイルをチェックインするまで、他のユーザーはそのファイルをチェックアウトできません。 ファイルを共有モードでチェックアウトする場合は、複数のユーザーが同じファイルをチェックアウトできます。 その場合、それぞれのユーザーがファイルをチェックインすると、ソース管理プロバイダーは、そのファイルを最新のサーバー バージョンにマージしようとします。 チェックインするバージョンと最新バージョンの間に競合がある場合は、ソース管理プロバイダーによって、競合を解決するための画面が表示されます。  
  
 このトピックでは、次の内容について紹介します。  
  
|トピック|説明|  
|-----------|-----------------|  
|[ファイルのチェックアウト](../../2014/database-engine/check-out-files.md)|ファイルを変更できるようにチェックアウトする方法を説明します。|  
|[チェックアウトの取り消し](../../2014/database-engine/undo-checkouts.md)|既存のチェックアウトを取り消す方法を説明します。|  
|[編集するファイルの自動的なチェックアウト](../../2014/database-engine/automatically-check-out-files-upon-edit.md)|ファイルの編集を始めるとファイルが自動的にチェックアウトされるようにソース管理を設定する方法を説明します。|  
  
## <a name="see-also"></a>参照  
 [チェックインを管理します。](../../2014/database-engine/manage-checkins.md)   
 [チェックインされているファイルの編集](../../2014/database-engine/edit-checked-in-files.md)  
  
  
