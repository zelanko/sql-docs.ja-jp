---
title: Oracle CDC インスタンス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ed71e8c4-e013-4bf2-8b6c-1e833ff2a41d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 03ccf5f5bae37238e59a0e96b4d53314b0e4906f
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52769094"
---
# <a name="the-oracle-cdc-instance"></a>Oracle CDC インスタンス
  Oracle CDC インスタンスは、単一の Oracle ソース データベースからキャプチャされた変更を処理するために、Oracle CDC Service によって作成されたプロセスです。 Oracle CDC インスタンスは、その構成を **cdc.xdbcdc_config** テーブルから取得し、その状態を **cdc.xdbcdc_state** テーブルで維持します。 これらのテーブルは、Oracle CDC インスタンスを定義する CDC データベースの一部です。 xdbcdc データベースおよびテーブルの詳細については、「 [The CDC Databases](the-oracle-cdc-service.md)」を参照してください。  
  
 Oracle CDC インスタンスによって実行されるタスクを次に示します。  
  
-   **サービスのスタートアップの検証の処理**:CDC インスタンスにから構成を読み込み、開始時に、 **xdbcdc_config**テーブルし、一連の実行状態検証ことを確認します、CDC インスタンスの永続化された状態に一貫性し、処理を開始できます。変更します。  
  
-   **変更のキャプチャの準備**:場合、検証が正常に、Oracle CDC インスタンスのスキャンすべて現在定義されているキャプチャ インスタンスのと、Oracle LogMiner クエリおよび変更のキャプチャに必要なその他のサポート構造を準備します。 また、Oracle インスタンスは Oracle CDC インスタンスが最後に実行されたときに保存された内部キャプチャ状態を再度読み込みます。  
  
-   **Oracle からの変更のキャプチャ**:Oracle CDC インスタンス Oracle LogMiner 機能を利用して Oracle からの変更をプール トランザクションのコミットに従ってそれらの注文しトランザクションの時刻を変更し、書き込みます、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC データベースのテーブルを変更します。  
  
-   **サービスのシャット ダウンの処理**:Oracle CDC インスタンスのライフ サイクルは、Oracle CDC Service によって管理されます。 シャットダウンを要求された場合、Oracle CDC インスタンスは次のタスクを実行します。  
  
    -   Oracle トランザクション ログからの読み取りを停止します。  
  
    -   完了した Oracle トランザクションの CDC データベースへの書き込みを停止します。  
  
    -   必要に応じて、現在のトランザクションの CDC データベースへの書き込みが終了するまで、最大で 30 秒待機します。 30 秒以上が経過した場合、書き込みはキャンセルされ、トランザクションはロールバックされます (CDC インスタンスが再起動したときに再試行されます)。  
  
    -   個別のスレッドで、ステージングされたトランザクション テーブルに最大で 30 秒間、メモリにキャッシュされたレコードをできるだけ多く書き込み (最も古いトランザクションから最新のトランザクションの順)、 **xdbcdc_state** テーブルを更新してすべての変更をコミットします。  
  
-   **構成の変更の処理**:Oracle CDC インスタンスは、CDC Service からかに新しいバージョンを検出することにより、構成の変更に関する通知を受け取る、 **cdc.xdbcdc_config**テーブル。 ほとんどの変更では、Oracle CDC インスタンスを再起動する必要はありません (キャプチャ インスタンスの追加または削除など)。 しかし、Oracle 接続文字列やアクセス資格情報の変更など、一部の変更では、Oracle CDC インスタンスを再起動する必要があります。  
  
-   **復旧の処理**:内部状態が復元された Oracle CDC インスタンスの開始時に、 **xdbcdc_state**と**xdbcdc_staged_transactions**テーブル。 状態が復元されると、CDC インスタンスは通常どおり実行されます。  
  
## <a name="see-also"></a>参照  
 [エラー処理](error-handling.md)  
  
  
