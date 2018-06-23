---
title: ファイルをソース管理から除外 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- excluding files from source control
- source controls [SQL Server Management Studio], file exclusions
ms.assetid: 7dcb6514-db5c-49eb-8b5a-2c766ce39aa7
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 597be5211a36e42320f3f7601c052121ef8aa2a4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173311"
---
# <a name="exclude-files-from-source-control"></a>ソース管理からのファイルの除外
  作業しているソリューションには、ソース管理サービスを必要としないファイルが含まれているを使って、**ソース管理から除外**コマンドをソース管理からファイルを除外します。 ファイルを除外すると、そのファイルは [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe データベースに残りますが、プロジェクトと共にチェックインまたはチェックアウトされなくなります。  
  
 使用する必要があります、**ソース管理から除外**生成されたファイルでのみコマンド。 いずれかの完全再作成することによって生成されたファイルは[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]ソリューション内の別のファイルの内容を基にします。  
  
### <a name="to-exclude-a-file-from-source-control"></a>ソース管理からファイルを除外するには  
  
1.  ソリューション エクスプローラーで、除外するファイルを選択します。  
  
2.  **ファイル** メニューのをポイント**ソース管理**、クリックして**除外** *\<ファイル名 >* **からソース管理**です。  
  
## <a name="see-also"></a>参照  
 [ソース管理の基礎](../../2014/database-engine/source-control-basics.md)   
 [ソース管理のオプションを設定します。](../../2014/database-engine/set-source-control-options.md)   
 [ソース管理接続の変更](../../2014/database-engine/change-source-control-connections.md)  
  
  