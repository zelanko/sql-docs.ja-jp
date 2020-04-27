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
manager: craigg
ms.openlocfilehash: 84d04729e2f4c00c5d127a706727567c44855cd6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66093677"
---
# <a name="only-sysadmin-users-can-write-job-step-log-files-to-the-file-system"></a>sysadmin ユーザーのみがジョブ ステップのログ ファイルをファイル システムに書き込むことができる
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、オプションで各ジョブ ステップのログが書き込まれます。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント  
  
## <a name="description"></a>説明  
 で[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]は[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、エージェントは、 **sysadmin**固定サーバーロールのメンバーが所有するジョブのログをファイルシステムに書き込むことができます。 ジョブの所有者が**sysadmin**ロールのメンバーではなく、プロキシアカウントが有効になって[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]いる場合、エージェントはプロキシアカウントの資格情報を使用してファイルシステムにログを書き込むことができます。  
  
 アップグレード後に、 **sysadmin**固定サーバーロールのメンバーではないユーザーが所有するジョブは、ログをファイルシステムに書き込むことができなくなります。 代わりに、これらのユーザーは、 **msdb**データベースのテーブルにログを書き込むオプションを選択できます。 **Sysadmin**ロールのメンバーは、ログファイルをファイルシステムに書き込むことができます。  
  
## <a name="corrective-action"></a>修正措置  
 アップグレード後、 **sysadmin**ロールのメンバーではないユーザーが所有するジョブは引き続き実行されますが、ログは作成されません。 ジョブステップをテーブルに記録するには、 **sysadmin**ロールのメンバーでないユーザーがジョブを手動で更新する必要があります。  
  
 詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「ジョブの作成」、「ジョブ ステップの作成」、および「複数のジョブ ステップの処理」の各トピックを参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server エージェントのアップグレードに関する問題](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
