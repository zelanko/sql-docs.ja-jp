---
title: "エンタープライズ全体の管理の自動化 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 618e199812a39ec29e032f8371419ec6184c713f
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="automated-administration-across-an-enterprise"></a>エンタープライズ全体の管理の自動化
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] の複数のインスタンスにわたって管理を自動化することを*マルチサーバー管理*といいます。 次の場合に、マルチサーバー管理を行います。  
  
-   2 台以上のサーバーを管理する場合  
  
-   データ ウェアハウジングのために、企業サーバーの情報フローをスケジュールする場合  
  
マルチサーバー管理機能を活用するには、1 台以上のマスター サーバーと 1 台以上の対象サーバーが必要です。 マスター サーバーは、対象サーバーに対してジョブを分散し、対象サーバーからイベントを受け取ります。 また、マスター サーバーは、対象サーバーで実行されるジョブについて、ジョブ定義の中央コピーも保存します。 対象サーバーは、定期的にマスター サーバーに接続して、ジョブのスケジュールを更新します。 マスター サーバー上に新しいジョブがあれば、対象サーバーはそのジョブをダウンロードします。 対象サーバーは、ジョブを完了した後、マスター サーバーに再接続してジョブのステータスをレポートします。 データベース関連アクティビティを実行するときはジョブの定義が同じでなければならないことに注意してください。  
  
次の図は、マスター サーバーと対象サーバーの関係を示します。  
  
![マルチ サーバー管理構成](../../ssms/agent/media/multisvr.gif "マルチ サーバー管理構成")  
  
大企業の複数の部門別サーバーを管理する場合は、次のアイテムを定義できます。  
  
-   複数のジョブ ステップから構成される 1 つのバックアップ ジョブ  
  
-   バックアップ エラーが発生した場合に通知するオペレーター  
  
-   バックアップ ジョブの実行スケジュール  
  
マスター サーバーにこのバックアップ ジョブを 1 回書き込んでから、各部門別サーバーを対象サーバーとして登録します。 この登録以降は、ジョブを一度しか定義しなくても、すべての部門別サーバーで同じバックアップ ジョブが実行されます。  
  
> [!NOTE]  
> マルチサーバー管理機能は、sysadmin ロールのメンバーを対象としています。 ただし、対象サーバー上の sysadmin ロールのメンバーは、マスター サーバーから、対象サーバーで実行される操作を変更することはできません。 このセキュリティ措置によって、ジョブ ステップが誤って削除されたり、対象サーバー上の操作が中断したりすることを防止できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
[マルチサーバー環境の作成](../../ssms/agent/create-a-multiserver-environment.md)  
マスター サーバーおよび対象サーバーを作成および管理する方法について説明します。  
  
[マルチサーバー環境に適した SQL Server エージェント サービス アカウントの選択](../../ssms/agent/choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスに管理者以外の Windows アカウントまたはローカル システム アカウントを使用することによる、マルチサーバー環境への影響について説明します。  
  
[対象サーバーでの暗号化オプションの設定](../../ssms/agent/set-encryption-options-on-target-servers.md)  
対象サーバーでの[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントの MsxEncryptChannelOptions レジストリ サブキーの設定について説明します。  
  
[エンタープライズ全体におけるジョブの管理](../../ssms/agent/manage-jobs-across-an-enterprise.md)  
ジョブ ステータスの確認、ジョブの対象サーバーの変更、対象サーバーのクロックの同期、およびマスター サーバーの現在のジョブ ステータスに対するポーリングについて説明します。  
  
[プロキシを使用するマルチサーバー ジョブのトラブルシューティング](../../ssms/agent/troubleshoot-multiserver-jobs-that-use-proxies.md)  
プロキシを使用しているマルチサーバー ジョブに障害が発生した場合のトラブルシューティングについて説明します。  
  
[サーバーのポーリング](../../ssms/agent/poll-servers.md)  
対象サーバーをマスター サーバーに明示的および暗黙的にポーリングして、ジョブ情報の同期をとる方法について説明します。  
  
[イベントの管理](../../ssms/agent/manage-events.md)  
対象サーバーからマスター サーバーに転送されるイベントについて説明します。  
  
[企業全体の自動管理のチューニング](../../ssms/agent/tune-automated-administration-across-an-enterprise.md)  
マルチサーバー環境で自動化された管理により [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]の自己チューニング機能を活用する方法について説明します。  
  
## <a name="see-also"></a>参照  
[SQL Server データベース エンジンのインストールに関する旧バージョンとの互換性のトピック](http://msdn.microsoft.com/en-us/10de5ec6-d3cf-42ef-aa62-1bdf3fbde841)  
[サーバーの登録](http://msdn.microsoft.com/en-us/c2a2513e-fa09-419c-99e7-a12d57c5a0db)  
[sp_add_targetservergroup](http://msdn.microsoft.com/en-us/acb69343-d766-46ff-b771-0c7655c5231a)  
[sp_delete_targetserver](http://msdn.microsoft.com/en-us/cc438701-ad91-419d-9f23-ebc4c548c700)  
[sp_delete_targetservergroup](http://msdn.microsoft.com/en-us/d8dd838e-64aa-419f-9ccb-ff04908cf3e4)  
[sp_help_downloadlist](http://msdn.microsoft.com/en-us/745b265b-86e8-4399-b928-c6969ca1a2c8)  
[sp_help_jobserver](http://msdn.microsoft.com/en-us/57971787-f9f5-4199-9f64-c2b61a308906)  
[sp_help_targetservergroup](http://msdn.microsoft.com/en-us/ec3a4a68-b591-431c-9518-053ede522d0c)  
[sp_resync_targetserver](http://msdn.microsoft.com/en-us/40e44df7-d3e3-44ee-b149-08aba629a21f)  
[sp_update_targetservergroup](http://msdn.microsoft.com/en-us/4ac65ed6-e07e-40e4-a282-13bfd92dfa41)  
[sysjobservers](http://msdn.microsoft.com/en-us/9abcc20f-a421-4591-affb-62674d04575e)  
[syslogins](http://msdn.microsoft.com/en-us/4cb34f17-a4bb-469f-a218-71f074e6308f)  
[systargetservers](http://msdn.microsoft.com/en-us/479d1314-be37-4d19-ac9c-419fc9110e53)  
  

