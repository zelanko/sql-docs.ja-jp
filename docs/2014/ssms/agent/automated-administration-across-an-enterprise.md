---
title: エンタープライズ全体の管理の自動化 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- enterprise automatic administration [SQL Server]
- multiserver administration [SQL Server]
- SQL Server Agent jobs, multiserver administration
- jobs [SQL Server Agent], multiserver administration
- master servers [SQL Server], about master servers
- target servers [SQL Server], about target servers
- master servers [SQL Server]
- multiple instances of SQL Server
- target servers [SQL Server]
ms.assetid: 44d8365b-42bd-4955-b5b2-74a8a9f4a75f
caps.latest.revision: 40
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c3b9d1885aefc738355f9f891680ebcfaf9d19a2
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "43813068"
---
# <a name="automated-administration-across-an-enterprise"></a>エンタープライズ全体の管理の自動化
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の複数のインスタンスにわたって管理を自動化することを*マルチサーバー管理*といいます。 次の場合に、マルチサーバー管理を行います。  
  
-   2 台以上のサーバーを管理する場合  
  
-   データ ウェアハウジングのために、企業サーバーの情報フローをスケジュールする場合  
  
> [!NOTE]  
>  一部として[!INCLUDE[msCoName](../../includes/msconame-md.md)]、所有権の総コストを削減する継続的な取り組み[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]2 つの機能が導入されました: ポリシー ベースの管理と構成サーバーとサーバーを使用するマルチ サーバー クエリに呼び出されるサーバーを管理する方法グループ。 この 2 つの機能は、ここで説明する機能の一部と組み合わせたり、それらの代わりとして使用したりすることができます。 詳細については、次を参照してください。[でポリシー ベースの管理サーバーの管理](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)と[複数サーバーを使用して中央管理サーバーの管理](../../relational-databases/administer-multiple-servers-using-central-management-servers.md)します。  
  
 マルチサーバー管理機能を活用するには、1 台以上のマスター サーバーと 1 台以上の対象サーバーが必要です。 マスター サーバーは、対象サーバーに対してジョブを分散し、対象サーバーからイベントを受け取ります。 また、マスター サーバーは、対象サーバーで実行されるジョブについて、ジョブ定義の中央コピーも保存します。 対象サーバーは、定期的にマスター サーバーに接続して、ジョブのスケジュールを更新します。 マスター サーバー上に新しいジョブがあれば、対象サーバーはそのジョブをダウンロードします。 対象サーバーは、ジョブを完了した後、マスター サーバーに再接続してジョブのステータスをレポートします。  
  
 次の図は、マスター サーバーと対象サーバーの関係を示します。  
  
 ![マルチ サーバー管理構成](../../database-engine/media/multisvr.gif "マルチ サーバー管理構成")  
  
 大企業の複数の部門別サーバーを管理する場合は、次のアイテムを定義できます。  
  
-   複数のジョブ ステップから構成される 1 つのバックアップ ジョブ  
  
-   バックアップ エラーが発生した場合に通知するオペレーター  
  
-   バックアップ ジョブの実行スケジュール  
  
 マスター サーバーにこのバックアップ ジョブを 1 回書き込んでから、各部門別サーバーを対象サーバーとして登録します。 この登録以降は、ジョブを一度しか定義しなくても、すべての部門別サーバーで同じバックアップ ジョブが実行されます。  
  
> [!NOTE]  
>  マルチサーバー管理機能は、sysadmin ロールのメンバーを対象としています。 ただし、対象サーバー上の sysadmin ロールのメンバーは、マスター サーバーから、対象サーバーで実行される操作を変更することはできません。 このセキュリティ措置によって、ジョブ ステップが誤って削除されたり、対象サーバー上の操作が中断したりすることを防止できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [マルチサーバー環境の作成](create-a-multiserver-environment.md)  
 マスター サーバーおよび対象サーバーを作成および管理する方法について説明します。  
  
 [マルチサーバー環境に適した SQL Server エージェント サービス アカウントの選択](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェント サービスに管理者以外の Windows アカウントまたはローカル システム アカウントを使用することによる、マルチサーバー環境への影響について説明します。  
  
 [対象サーバーでの暗号化オプションの設定](set-encryption-options-on-target-servers.md)  
 対象サーバーでの[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントの MsxEncryptChannelOptions レジストリ サブキーの設定について説明します。  
  
 [エンタープライズ全体におけるジョブの管理](manage-jobs-across-an-enterprise.md)  
 ジョブ ステータスの確認、ジョブの対象サーバーの変更、対象サーバーのクロックの同期、およびマスター サーバーの現在のジョブ ステータスに対するポーリングについて説明します。  
  
 [プロキシを使用するマルチサーバー ジョブのトラブルシューティング](troubleshoot-multiserver-jobs-that-use-proxies.md)  
 プロキシを使用しているマルチサーバー ジョブに障害が発生した場合のトラブルシューティングについて説明します。  
  
 [サーバーのポーリング](poll-servers.md)  
 対象サーバーをマスター サーバーに明示的および暗黙的にポーリングして、ジョブ情報の同期をとる方法について説明します。  
  
 [イベントの管理](manage-events.md)  
 対象サーバーからマスター サーバーに転送されるイベントについて説明します。  
  
 [企業全体の自動管理のチューニング](tune-automated-administration-across-an-enterprise.md)  
 マルチサーバー環境で自動化された管理により [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]の自己チューニング機能を活用する方法について説明します。  
  
## <a name="see-also"></a>参照  
 [SQL Server データベース エンジンの旧バージョンとの互換性](../../database-engine/sql-server-database-engine-backward-compatibility.md)   
 [サーバーの登録](../register-servers/register-servers.md)   
 [sp_add_targetservergroup &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-targetservergroup-transact-sql)   
 [sp_delete_targetserver &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-targetserver-transact-sql)   
 [sp_delete_targetservergroup &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-targetservergroup-transact-sql)   
 [sp_help_downloadlist &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-downloadlist-transact-sql)   
 [sp_help_jobserver &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobserver-transact-sql)   
 [sp_help_targetservergroup &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-targetservergroup-transact-sql)   
 [sp_resync_targetserver &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql)   
 [sp_update_targetservergroup &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-targetservergroup-transact-sql)   
 [dbo.sysjobservers &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobservers-transact-sql)   
 [sys.syslogins &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-syslogins-transact-sql)   
 [dbo.systargetservers &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-tables/dbo-systargetservers-transact-sql)  
  
  
