---
title: 別々のドライブへのデータ ファイルとログ ファイルの配置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 6cbedc27-4d77-44ad-bed2-c23b628475a7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d06087da1167c9988c8c08515acdfedb65afa090
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85011012"
---
# <a name="place-data-and-log-files-on-separate-drives"></a>別々のドライブへのデータ ファイルとログ ファイルの配置
  このルールでは、データ ファイルとログ ファイルが別々の論理ドライブに配置されているかどうかを確認します。 データ ファイルとログ ファイルの両方を同じデバイスに配置すると、そのデバイスで競合が発生し、パフォーマンスが低下する可能性があります。 ファイルを別々のドライブに配置すると、I/O 動作をデータ ファイルとログ ファイルの両方で同時に行うことができます。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 新しいデータベースを作成するときに、データ用とログ用に別々のドライブを指定します。 データベースの作成後にファイルを移動するには、データベースをオフラインにする必要があります。 次のいずれかの方法を使用して、ファイルを移動します。  
  
> [!NOTE]  
>  このポリシーでは、マウント ポイントを介して別個の物理デバイスを検出することはできません。  
  
-   RESTORE DATABASE ステートメントで WITH MOVE オプションを使用してバックアップからデータベースを復元します。  
  
-   データベースをデタッチしてから、データ デバイス用とログ デバイス用に別々の場所を指定してデータベースをアタッチします。  
  
-   MODIFY FILE オプションを指定して ALTER DATABASE ステートメントを実行し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを再起動して、新しい場所を指定します。  
  
## <a name="for-more-information"></a>詳細情報  
 [データベース ファイルの移動](../databases/move-database-files.md)  
  
 [ユーザー データベースの移動](../databases/move-user-databases.md)  
  
 [データベースのデタッチとアタッチ &#40;SQL Server&#41;](../databases/database-detach-and-attach-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [ポリシーベースの管理を使用したベスト プラクティスの監視と実行](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
