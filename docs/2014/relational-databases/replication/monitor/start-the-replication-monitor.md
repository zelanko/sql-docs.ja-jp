---
title: レプリケーション モニターの開始 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor, starting
ms.assetid: e037bd27-cc87-4ee9-9e5f-83f6d717cfa4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cff23206923825d0e86e47ad6921c19f45e68b35
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85068624"
---
# <a name="start-the-replication-monitor"></a>レプリケーション モニターの開始
  レプリケーション モニターは、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] から [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]の任意のインスタンスに対して起動するか、コマンド プロンプトから起動できます。 レプリケーション モニターを起動した後、1 つ以上のパブリッシャーをモニターに追加します。 詳細については、「 [レプリケーション モニターのパブリッシャーの追加および削除](add-and-remove-publishers-from-replication-monitor.md)」を参照してください。  
  
### <a name="to-start-replication-monitor-from-sql-server-management-studio"></a>SQL Server Management Studio からレプリケーション モニターを起動するには  
  
1.  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]のインスタンスに接続して、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーまたはそのサブフォルダーを右クリックして、 **[レプリケーション モニターの起動]** をクリックします。  
  
### <a name="to-start-replication-monitor-from-the-command-prompt"></a>コマンド プロンプトからレプリケーション モニターを起動するには  
  
1.  コマンド プロンプトで、ツールをインストールしたディレクトリに移動します。 既定のパスは [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]Tools\Binn\ です。  
  
2.  sqlmonitor.exe を実行します。  
  
## <a name="see-also"></a>参照  
 [レプリケーションの監視](../monitoring-replication.md)  
  
  
