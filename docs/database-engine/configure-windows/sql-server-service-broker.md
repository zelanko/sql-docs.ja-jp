---
title: SQL Server Service Broker | Microsoft Docs
ms.custom: 
ms.date: 08/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SQL13.SWB.SSBMSGTYPEPROPERTIES.GENERAL.F1
- SQL13.SWB.SSBCONTRACTPROPERTIES.GENERAL.F1
- SQL13.SWB.SSBQUEUEPROPERTIES.GENERAL.F1
- SQL13.SWB.SSBREMSVCBINDPROPERTIES.GENERAL.F1
- SQL13.SWB.SSBROUTEPROPERTIES.GENERAL.F1
- SQL13.SWB.SSBPRIORITYPROPERTIES.GENERAL.F1
- SQL13.SWB.SSBSERVICEPROPERTIES.GENERAL.F1
helpviewer_keywords:
- Broker See Service Broker
- SQL Server Service Broker
- Service Broker
ms.assetid: 8b8b3b57-fd46-44de-9a4e-e3a8e3999c1e
caps.latest.revision: "22"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 2c25c1fd1780e090a47e85264f4c579f52cdf0d5
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="sql-server-service-broker"></a>SQL Server Service Broker (SQL Server Service Broker)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSB](../../includes/sssb-md.md)] は、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のメッセージング アプリケーションおよびキューイング アプリケーションをネイティブで サポートします。 これにより、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] コンポーネントを使用して異種データベース間の通信を行う高度なアプリケーションを簡単に作成できるようになるため、 [!INCLUDE[ssSB](../../includes/sssb-md.md)] を使用すれば、信頼性の高い分散アプリケーションを簡単に開発できます。  
  
 アプリケーション開発者は、 [!INCLUDE[ssSB](../../includes/sssb-md.md)] を使用すれば、通信やメッセージングの複雑な内部のプログラミングを行わなくても、データ ワークロードを複数のデータベースに分散できます。 [!INCLUDE[ssSB](../../includes/sssb-md.md)] によってメッセージ交換のコンテキスト内で通信パスが処理されるので、開発やテストの作業を削減できます。 また、パフォーマンスも向上します。 たとえば、Web サイトをサポートするフロントエンド データベースで情報の記録を行い、処理負荷の高いタスクはバックエンド データベースのキューに送信できます。 [!INCLUDE[ssSB](../../includes/sssb-md.md)] では、すべてのタスクがトランザクションのコンテキストで管理されるため、信頼性と技術的な一貫性を確保できます。  
  
## <a name="where-is-the-documentation-for-service-broker"></a>Service Broker のドキュメントの格納場所  
 [!INCLUDE[ssSB](../../includes/sssb-md.md)] のリファレンス ドキュメントは [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のドキュメントに含まれています。 リファレンス ドキュメントには次のセクションがあります。  
  
-   CREATE、ALTER、および DROP ステートメントの[データ定義言語 &#40;DDL&#41; ステートメント &#40;Transact-SQL&#41;](~/mdx/mdx-data-definition-statements-mdx.md)   
  
-   [Service Broker のステートメント](../../t-sql/statements/service-broker-statements.md)  
  
-   [Service Broker カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/service-broker-catalog-views-transact-sql.md)  
  
-   [Service Broker 関連の動的管理ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql.md)  
  
-   [ssbdiagnose ユーティリティ &#40;Service Broker&#41;](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
 [の概念、開発作業、および管理作業については、](http://go.microsoft.com/fwlink/?LinkId=231312) 以前に公開されたドキュメント [!INCLUDE[ssSB](../../includes/sssb-md.md)] を参照してください。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は [!INCLUDE[ssSB](../../includes/sssb-md.md)] においてわずかな変更しか加えられていないため、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]用のドキュメントは作成されていません。  
  
## <a name="whats-new-in-service-broker"></a>Service Broker の新機能  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]で導入された大きな変更はありません。  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]では、以下の変更が導入されました。  
  
### <a name="messages-can-be-sent-to-multiple-target-services-multicast"></a>メッセージを複数の対象サービスに送信可能 (マルチキャスト)  
 [SEND &#40;Transact-SQL&#41;](../../t-sql/statements/send-transact-sql.md) ステートメントの構文が拡張され、複数のメッセージ交換ハンドルをサポートすることにより、マルチキャストが有効になりました。  
  
### <a name="queues-expose-the-message-enqueued-time"></a>メッセージがエンキューされている時間の公開  
 メッセージがキューに格納されている時間を示す新しい列 **message_enqueue_time**がキューに追加されました。  
  
### <a name="poison-message-handling-can-be-disabled"></a>有害メッセージの処理の無効化が可能  
 [CREATE QUEUE &#40;Transact-SQL&#41;](../../t-sql/statements/create-queue-transact-sql.md) ステートメントおよび [ALTER QUEUE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-queue-transact-sql.md) ステートメントでは、`POISON_MESSAGE_HANDLING (STATUS = ON | OFF)` 句を追加することによって有害メッセージの処理を無効化できるようになりました。 カタログ ビュー **sys.service_queues** に、有害メッセージの処理が有効であるか無効であるかを示す **is_poison_message_handling_enabled** 列が追加されました。  
  
### <a name="always-on-support-in-service-broker"></a>Service Broker での Always On のサポート  
 詳細については、「 [Service Broker と Always On 可用性グループ (SQL Server)](../../database-engine/availability-groups/windows/service-broker-with-always-on-availability-groups-sql-server.md)」を参照してください。  
  
  

