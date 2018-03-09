---
title: "ユーティリティ コントロール ポイント データ ウェアハウスの構成 (SQL Server ユーティリティ) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: maintenance-plans
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2c6f050-8cdb-4b8e-ad38-4aae0a949847
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f4be33b398d7225125c68fadcdca5e334a309788
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="configure-your-utility-control-point-data-warehouse-sql-server-utility"></a>ユーティリティ コントロール ポイント データ ウェアハウスの構成 (SQL Server ユーティリティ)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージ インスタンスで収集されたデータは、ユーティリティ管理データ ウェアハウス (UMDW) に格納されます。UMDW ファイル名は sysutility_mdw です。  
  
 UMDW のデータ保持期間を構成できます。 詳細については、「[ユーティリティの管理 &#40;SQL Server Utility&#41;](http://msdn.microsoft.com/library/3e5a00c3-8905-40f0-9ddc-d924df9c2f0d)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のこのリリースで構成できない構成設定は次のとおりです。  
  
-   UMDW 名: Sysutility_mdw  
  
-   コレクション セットのアップロード頻度: 15 分ごと  
  
 UMDW ディレクトリ \<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\ (通常、\<System drive> は C:\ ドライブ) は構成可能です。 ログ ファイル Sysutility_mdw_\<GUID>_LOG は同じディレクトリにあります。  
  
> [!NOTE]  
>  UMDW (sysutility_mdw) ファイルの場所を変更するには、デタッチとアタッチを使用する方法と ALTER DATABASE を使用する方法があります。 ALTER DATABASE の使用をお勧めします。 詳細については、「[ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server ユーティリティの機能とタスク](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
  
