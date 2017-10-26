---
title: "別々のドライブへのデータ ファイルとログ ファイルの配置 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 6cbedc27-4d77-44ad-bed2-c23b628475a7
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d1105f11c98ac0b0c509f4c1d43a92ddd1a7a10c
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="place-data-and-log-files-on-separate-drives"></a>別々のドライブへのデータ ファイルとログ ファイルの配置
  このルールでは、データ ファイルとログ ファイルが別々の論理ドライブに配置されているかどうかを確認します。 データ ファイルとログ ファイルの両方を同じデバイスに配置すると、そのデバイスで競合が発生し、パフォーマンスが低下する可能性があります。 ファイルを別々のドライブに配置すると、I/O 動作をデータ ファイルとログ ファイルの両方で同時に行うことができます。  
  
## <a name="recommendations"></a>推奨事項  
 新しいデータベースを作成するときに、データ用とログ用に別々のドライブを指定します。 データベースの作成後にファイルを移動するには、データベースをオフラインにする必要があります。 次のいずれかの方法を使用してファイルを移動します。  
  
> [!NOTE]  
>  このポリシーでは、マウント ポイントを介して別個の物理デバイスを検出することはできません。  
  
-   RESTORE DATABASE ステートメントで WITH MOVE オプションを使用してバックアップからデータベースを復元します。  
  
-   データベースをデタッチしてから、データ デバイス用とログ デバイス用に別々の場所を指定してデータベースをアタッチします。  
  
-   MODIFY FILE オプションを指定して ALTER DATABASE ステートメントを実行し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを再起動して、新しい場所を指定します。  
  
## <a name="for-more-information"></a>詳細情報  
 [データベース ファイルの移動](../../relational-databases/databases/move-database-files.md)  
  
 [ユーザー データベースの移動](../../relational-databases/databases/move-user-databases.md)  
  
 [データベースのデタッチとアタッチ &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したベスト プラクティスの監視と実行](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  

