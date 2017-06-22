---
title: "メモリ最適化テーブルのストレージの構成 | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e005de0-3a77-4b91-b497-14cc0f9f6605
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0250c8370960dc17adf13c020c51bfc603b111c8
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="configuring-storage-for-memory-optimized-tables"></a>メモリ最適化テーブルのストレージの構成
  記憶域の容量と 1 秒間の入出力操作 (IOPS) を構成する必要があります。  
  
## <a name="storage-capacity"></a>記憶域の容量  
 [メモリ最適化テーブルのメモリ必要量の推定](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md) の情報を使用して、データベースの持続性のあるメモリ最適化テーブルのメモリ内サイズを推定します。 インデックスはメモリ最適化テーブルに対して永続化されないため、インデックスのサイズは含めません。 サイズを確認した後には、持続性のあるメモリ内テーブルのサイズの 4 倍のディスク領域を提供する必要があります。  
  
## <a name="storage-iops"></a>記憶域の IOPS  
 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] は、ワークロードのスループットを大幅に上げることができます。 したがって、IO がボトルネックになっていないことを確認してください。  
  
-   ディスク ベース テーブルをメモリ最適化テーブルに移行するときは、トランザクション ログ アクティビティの増加をサポートできる記憶メディアにトランザクション ログがあることを確認してください。 たとえば、記憶メディアが 100 MB/秒のトランザクション ログの処理をサポートし、その結果としてメモリ最適化テーブルが 5 倍優れたパフォーマンスをもたらす場合、トランザクション ログ アクティビティがパフォーマンスのボトルネックになることを防ぐために、トランザクション ログの記憶メディアでも、5 倍のパフォーマンス向上をサポートできる必要があります。  
  
-   メモリ最適化テーブルは、1 つまたは複数のコンテナーに分散されたファイルに保存されます。 各コンテナーは、通常、独自のスピンドルにマップする必要があり、増加する記憶域容量と IOPS の向上の両方のために使用されます。 記憶メディアのシーケンシャル IOPS が、トランザクション ログのスループットの増加量の 3 倍をサポートできることを確認する必要があります。  
  
     たとえば、メモリ最適化テーブルがトランザクション ログで 500 MB/秒のアクティビティを生成する場合、メモリ最適化テーブルのストレージは 1.5 GB/秒の IOPS をサポートする必要があります。 トランザクション ログのスループットの増加量の 3 倍をサポートする必要性は、次の観察点に由来します。すなわち、データとデルタ ファイルのペアは、まず初期データと共に書き込まれ、それからマージ操作の一環として読み取り/再書き込みされる必要があるという点です。  
  
     記憶域の IOPS を見積もる際のもう 1 つの要因は、メモリ最適化テーブルの復旧時間です。 持続性のあるテーブルからのデータは、データベースがアプリケーションで使用される前にメモリに読み込む必要があります。 一般的に、メモリ最適化テーブルへのデータの読み込みは IOPS の速度で実行できます。 それで、持続性のあるメモリ最適化テーブルの合計の記憶域が 60 GB で、1 分でこのデータを読み込めるようにする場合は、記憶域の IOPS を 1 GB/秒に設定する必要があります。  
  
-   スピンドルの数が偶数の場合、SQL Server 2014 とは異なり、チェックポイント ファイルがすべてのスピンドル間で均等に分散されます。  
  
## <a name="encryption"></a>暗号化  
 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] では、メモリ最適化テーブルのストレージの暗号化は、データベースで TDE を有効化する際に行われます。 詳細については、「[透過的なデータ暗号化 &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption-tde.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [メモリ最適化オブジェクト用ストレージの作成と管理](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
