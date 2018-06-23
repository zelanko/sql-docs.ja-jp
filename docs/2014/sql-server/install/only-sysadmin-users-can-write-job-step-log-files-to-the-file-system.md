---
title: Sysadmin ユーザーは、ファイル システムにジョブ ステップ ログ ファイルを書き込むことができますのみ |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- job step log files [SQL Server Agent]
- log files [SQL Server Agent]
- writing job step log files
ms.assetid: d26a7cef-1a60-4c95-b9df-f8b4fec59f9b
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e0b7638bbbf33cdd820467cd21edc40a6f5c42ee
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085346"
---
# <a name="only-sysadmin-users-can-write-job-step-log-files-to-the-file-system"></a>sysadmin ユーザーのみがジョブ ステップのログ ファイルをファイル システムに書き込むことができる
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、オプションで各ジョブ ステップのログが書き込まれます。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント  
  
## <a name="description"></a>説明  
 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントは、のメンバーが所有するジョブをファイル システムにログを書き込むことができます、 **sysadmin**固定サーバー ロール。 ジョブの所有者がのメンバーではない場合、 **sysadmin**ロールと、プロキシ アカウントが有効なかどうかは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントはプロキシ アカウントの資格情報を使用して、ファイル システムにログを記述することができます。  
  
 アップグレードした後、メンバーではないユーザーによって所有されているジョブの**sysadmin**固定サーバー ロール、ファイル システムにログを書き込むことができなくします。 これらのユーザーが内のテーブルにログを書き込んだりするオプションを選択する代わりに、 **msdb**データベース。 メンバー、 **sysadmin**ロールは、ログ ファイルをファイル システムへの書き込みはまだことができます。  
  
## <a name="corrective-action"></a>修正措置  
 アップグレードした後、メンバーではないユーザーによって所有されているジョブの**sysadmin**ロールを実行するには続行されますが、ログは作成されません。 メンバーではないユーザー、テーブルへのジョブ ステップのログインの**sysadmin**ロールは、ジョブを手動で更新する必要があります。  
  
 詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「ジョブの作成」、「ジョブ ステップの作成」、および「複数のジョブ ステップの処理」の各トピックを参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server エージェントのアップグレードに関する問題](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  