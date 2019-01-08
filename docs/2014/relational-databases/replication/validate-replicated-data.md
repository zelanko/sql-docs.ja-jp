---
title: レプリケートされたデータの検証 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- inline data validation [SQL Server replication]
- administering replication, validating data
- replication [SQL Server], validating data
- transactional replication, validating data
- validating data
- merge replication data validation [SQL Server replication]
- merge replication data validation [SQL Server replication], about data validation
- validating replicated data
ms.assetid: f7500a2b-61cb-41b5-816d-27609a6c58e7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 84ffe2ad4be91f8a05e4bbbd84b2ad5a67cb09a4
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52792494"
---
# <a name="validate-replicated-data"></a>レプリケートされたデータの検証
  トランザクション レプリケーションとマージ レプリケーションを使用すると、サブスクライバーのデータがパブリッシャーのデータと一致するかどうかを検証できます。 検証は、1 つのパブリケーションの特定のサブスクリプション、またはすべてのサブスクリプションに対して行うことができます。 次のいずれかの種類の検証を指定すると、ディストリビューション エージェントまたはマージ エージェントは次回の実行時にデータを検証します。  
  
-   行数のみ。 サブスクライバーのテーブルにパブリッシャーのテーブルと同じ数の行があるかどうかを検証しますが、行の内容が一致するかどうかについては検証しません。 行数の確認は、データに問題があるかどうかを調べる手軽な検証方法です。  
  
-   行数とバイナリ チェックサム。 パブリッシャーとサブスクライバーの行数に加え、チェックサム アルゴリズムを使用して、すべてのデータのチェックサムが計算されます。 行数の検証で失敗となった場合、チェックサムは実行されません。  
  
 サブスクライバーとパブリッシャーのデータが一致するかどうかの検証に加え、マージ レプリケーションでは、各サブスクライバーに対してデータが正しくパーティション分割されているかどうかを検証する機能も用意されています。 詳細については、「[Validate Partition Information for a Merge Subscriber](validate-partition-information-for-a-merge-subscriber.md)」 (マージ サブスクライバーのパーティション情報の検証) を参照してください。  
  
 **データを検証するには**  
  
 サブスクリプションのすべてのアーティクルを検証するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、ストアド プロシージャ、またはレプリケーション管理オブジェクト (RMO) を使用します。 詳細については、「 [Validate Data at the Subscriber](validate-data-at-the-subscriber.md)」を参照してください。 スナップショット パブリケーションおよびトランザクション パブリケーションの個々のアーティクルを検証するには、ストアド プロシージャを使用する必要があります。  
  
## <a name="data-validation-results"></a>データ検証の結果  
 検証が完了すると、ディストリビューション エージェントまたはマージ エージェントは成功または失敗に関するメッセージをログに記録します (レプリケーションでは失敗した行については報告されません)。 これらのメッセージは [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、レプリケーション モニター、およびレプリケーション システム テーブルで参照できます。 操作方法に関する上記のトピックは、検証の実行方法と結果を表示する方法を示しています。  
  
 データ検証の問題に対処するために、次の点を検討してください。  
  
-   構成というレプリケーション警告**レプリケーション。サブスクライバーでは、データの検証が失敗した**エラーの場合に通知されるようにします。 詳細については、次を参照してください。 [構成の定義済みのレプリケーションの警告&#40;SQL Server Management Studio & #41 41(administration/configure-predefined-replication-alerts-sql-server-management-studio.md) します。  
  
-   検証の失敗はアプリケーションにとって問題となりますか? 検証の失敗が問題となる場合、データを手動で更新して同期するか、サブスクリプションを再初期化してください。  
  
    -   データを更新するには [tablediff ユーティリティ](../../tools/tablediff-utility.md)を使用します。 このユーティリティの使用方法の詳細については、「[Compare Replicated Tables for Differences &#40;Replication Programming&#41;](administration/compare-replicated-tables-for-differences-replication-programming.md)」 (レプリケートされたテーブルを比較して相違があるかどうかを確認する &#40;レプリケーション プログラミング&#41;) を参照してください。  
  
    -   再初期化の詳細については、「[Reinitialize Subscriptions](reinitialize-subscriptions.md)」 (サブスクリプションの再初期化) を参照してください。  
  
## <a name="considerations-for-data-validation"></a>データ検証に関する注意点  
 データの検証に際しては、次の点に注意してください。  
  
-   データを検証する前にサブスクライバー側のすべての更新操作を停止する必要があります (検証実行時にパブリッシャー側の操作を停止する必要はありません)。  
  
-   チェックサムおよびバイナリ チェックサムを使用した検証を大規模なデータセットに対して行う場合には、大量のプロセッサ リソースが必要になるので、レプリケーションで使用するサーバーの利用状況が最小のときに検証を行うようにスケジュールする必要があります。  
  
-   レプリケーションはテーブルのみを検証します。スキーマのみのアーティクル (ストアド プロシージャなど) がパブリッシャーとサブスクライバーで同じであるかどうかは検証しません。  
  
-   バイナリ チェックサムは、パブリッシュされたどのテーブルでも使用できます。 チェックサムは、列フィルターの設定されたテーブル、または列オフセットが異なる論理テーブル構造 (列を削除または追加する ALTER TABLE ステートメントの結果) は検証できません。  
  
-   レプリケーションの検証を使用して、`checksum`と**binary_checksum**関数。 各関数の動作については、「[CHECKSUM &#40;Transact-SQL&#41;](/sql/t-sql/functions/checksum-transact-sql)」と「[BINARY_CHECKSUM  &#40;Transact-SQL&#41;](/sql/t-sql/functions/binary-checksum-transact-sql)」を参照してください。  
  
-   バイナリ チェックサムまたはチェックサムを使用した検証では、データ型がサブスクライバー側とパブリッシャー側とで異なる場合には、誤ってエラーを報告することがあります。 これは、次のいずれかの場合に発生する可能性があります。  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の以前のバージョンのデータ型をマップするスキーマ オプションを明示的に設定している場合。  
  
    -   マージ パブリケーションのパブリケーションの互換性レベルを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の以前のバージョンに設定し、パブリッシュされたテーブルに、このバージョンに対してマップする必要がある 1 つ以上のデータ型が含まれている場合。  
  
    -   サブスクリプションを手動で初期化し、サブスクライバーで異なるデータ型を使用している場合。  
  
-   バイナリ チェックサムおよびチェックサムによる検証は、トランザクション レプリケーションの変換可能なサブスクリプションではサポートされていません。  
  
-   検証は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のサブスクライバーにレプリケートされたデータに対してはサポートされていません。  
  
## <a name="how-data-validation-works"></a>データ検証の動作  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、パブリッシャー側の行数やチェックサムを計算し、それらの値をサブスクライバー側で計算された行数やチェックサムと比較することで、データの検証を行います。 一方の値はパブリケーション テーブル全体に対して計算され、もう一方の値はサブスクリプション テーブル全体に対して計算されます。ただし、`text` 列、`ntext` 列、または `image` 列にあるデータはその計算には含まれません。  
  
 計算が行われている間は、行数またはチェックサムの計算が行われているテーブルに共有ロックが一時的にかかりますが、計算はすぐに終了し、通常、数秒で共有ロックは解除されます。  
  
 バイナリ チェックサムを使用する場合は、32 ビット CRC (冗長性検査) がデータ ページの物理的な行ではなく、列ごとに実行されます。 これにより、テーブルの列がデータ ページで物理的にどのような順序であっても、行については同じ CRC 値が計算されます。 バイナリ チェックサムを使用した検証は、パブリケーション上に行フィルターまたは列フィルターがある場合に使用できます。  
  
## <a name="see-also"></a>参照  
 [Best Practices for Replication Administration](administration/best-practices-for-replication-administration.md)  
  
  
