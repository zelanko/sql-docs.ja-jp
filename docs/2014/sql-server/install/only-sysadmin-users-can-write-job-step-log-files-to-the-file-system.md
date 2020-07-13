---
title: Sysadmin ユーザーのみがファイルシステムにジョブステップのログファイルを書き込むことができます |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- job step log files [SQL Server Agent]
- log files [SQL Server Agent]
- writing job step log files
ms.assetid: d26a7cef-1a60-4c95-b9df-f8b4fec59f9b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9e2bf5095ac1e6b67f6c6f3f87444879913916e1
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85012181"
---
# <a name="only-sysadmin-users-can-write-job-step-log-files-to-the-file-system"></a>sysadmin ユーザーのみがジョブ ステップのログ ファイルをファイル システムに書き込むことができる
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、オプションで各ジョブ ステップのログが書き込まれます。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント  
  
## <a name="description"></a>説明  
 では [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 、エージェントは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **sysadmin**固定サーバーロールのメンバーが所有するジョブのログをファイルシステムに書き込むことができます。 ジョブの所有者が**sysadmin**ロールのメンバーではなく、プロキシアカウントが有効になっている場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントはプロキシアカウントの資格情報を使用してファイルシステムにログを書き込むことができます。  
  
 アップグレード後に、 **sysadmin**固定サーバーロールのメンバーではないユーザーが所有するジョブは、ログをファイルシステムに書き込むことができなくなります。 代わりに、これらのユーザーは、 **msdb**データベースのテーブルにログを書き込むオプションを選択できます。 **Sysadmin**ロールのメンバーは、ログファイルをファイルシステムに書き込むことができます。  
  
## <a name="corrective-action"></a>修正措置  
 アップグレード後、 **sysadmin**ロールのメンバーではないユーザーが所有するジョブは引き続き実行されますが、ログは作成されません。 ジョブステップをテーブルに記録するには、 **sysadmin**ロールのメンバーでないユーザーがジョブを手動で更新する必要があります。  
  
 詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「ジョブの作成」、「ジョブ ステップの作成」、および「複数のジョブ ステップの処理」の各トピックを参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server エージェントのアップグレードに関する問題](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
