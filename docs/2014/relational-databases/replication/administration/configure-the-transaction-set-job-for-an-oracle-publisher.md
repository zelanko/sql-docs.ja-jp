---
title: Oracle パブリッシャーのトランザクションセットジョブの構成 (レプリケーション Transact-sql プログラミング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_publisherproperty
- Oracle publishing [SQL Server replication], configuring
ms.assetid: beea1a5c-0053-4971-a68f-0da53063fcbb
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 48282f08df588f54b6f03a0b99c58a2f0cf039ac
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67793545"
---
# <a name="configure-the-transaction-set-job-for-an-oracle-publisher-replication-transact-sql-programming"></a>Oracle パブリッシャー用のトランザクション セット ジョブの構成 (レプリケーション Transact-SQL プログラミング)
  **Xactset** ジョブは、Oracle パブリッシャーで実行されているレプリケーションがトランザクション セットを生成するために作成する Oracle データベース ジョブです。Oracle パブリッシャーにログ リーダー エージェントが接続されていない場合に使用されます。 このジョブは、レプリケーションのストアド プロシージャを使用し、ディストリビューターからプログラムによって有効化したり構成することができます。 詳細については、「[Performance Tuning for Oracle Publishers](../non-sql/performance-tuning-for-oracle-publishers.md)」 (Oracle パブリッシャーのパフォーマンス チューニング) を参照してください。  
  
### <a name="to-enable-the-transaction-set-job"></a>トランザクション セット ジョブを有効にするには  
  
1.  Oracle パブリッシャーで、 **job_queue_processes** 初期化パラメーターに、Xactset ジョブを実行できるだけの十分な値を設定します。 このパラメーターの詳細については、Oracle パブリッシャー用データベースのマニュアルを参照してください。  
  
2.  ディストリビューターで、[sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql) を実行します。 ** \@パブリッシャー**に Oracle パブリッシャーの名前、 ** \@propertyname**には値`xactsetbatching` 、 ** \@propertyvalue** `enabled`には値を指定します。  
  
3.  ディストリビューターで、[sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql) を実行します。 ** \@パブリッシャー**に Oracle パブリッシャーの名前を、 ** \@propertyname** `xactsetjobinterval`に値を、 ** \@propertyvalue**に対してジョブ間隔を分単位で指定します。  
  
4.  ディストリビューターで、[sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql) を実行します。 ** \@パブリッシャー**に Oracle パブリッシャーの名前、 ** \@propertyname**には値`xactsetjob` 、 ** \@propertyvalue** `enabled`には値を指定します。  
  
### <a name="to-configure-the-transaction-set-job"></a>トランザクション セット ジョブを構成するには  
  
1.  (省略可能) ディストリビューターで [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql) を実行します。 パブリッシャーの Oracle パブリッシャーの名前を指定します。 ** \@** これにより、パブリッシャーの **Xactset** ジョブのプロパティが返されます。  
  
2.  ディストリビューターで、[sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql) を実行します。 パブリッシャーの Oracle パブリッシャーの名前、 ** \@propertyname**に対して設定する Xactset ジョブプロパティの名前、および** \@propertyvalue**の新しい設定を指定します。 ** \@**  
  
3.  (省略可) 設定対象の各 Xactset ジョブ プロパティについて、手順 2. を繰り返します。 `xactsetjobinterval`プロパティを変更するときは、新しい間隔を有効にするために、Oracle パブリッシャーでジョブを再起動する必要があります。  
  
### <a name="to-view-properties-of-the-transaction-set-job"></a>トランザクション セット ジョブのプロパティを表示するには  
  
1.  ディストリビューターで [sp_helpxactsetjob](/sql/relational-databases/system-stored-procedures/sp-helpxactsetjob-transact-sql)を実行します。 パブリッシャーの Oracle パブリッシャーの名前を指定します。 ** \@**  
  
### <a name="to-disable-the-transaction-set-job"></a>トランザクション セット ジョブを無効にするには  
  
1.  ディストリビューターで、[sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql) を実行します。 ** \@パブリッシャー**に Oracle パブリッシャーの名前、 ** \@propertyname**には値`xactsetjob` 、 ** \@propertyvalue** `disabled`には値を指定します。  
  
## <a name="example"></a>例  
 次の例では、 `Xactset` ジョブを有効にし、実行間隔を 3 分に設定しています。  
  
 [!code-sql[HowTo#sp_enable_xactsetjob](../../../snippets/tsql/SQL15/replication/howto/tsql/enablexactsetjob.sql#sp_enable_xactsetjob)]  
  
## <a name="see-also"></a>参照  
 [Oracle パブリッシャーのパフォーマンスチューニング](../non-sql/performance-tuning-for-oracle-publishers.md)   
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)  
  
  
