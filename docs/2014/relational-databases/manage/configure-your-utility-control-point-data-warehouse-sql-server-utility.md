---
title: ユーティリティ コントロール ポイント データ ウェアハウスの構成 (SQL Server ユーティリティ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: c2c6f050-8cdb-4b8e-ad38-4aae0a949847
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f136f91f3f87d8072508a688db7ff9e496407607
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48168372"
---
# <a name="configure-your-utility-control-point-data-warehouse-sql-server-utility"></a>ユーティリティ コントロール ポイント データ ウェアハウスの構成 (SQL Server ユーティリティ)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージド インスタンスで収集されたデータは、ユーティリティ管理データ ウェアハウス (UMDW) に格納されます。UMDW ファイル名は sysutility_mdw です。  
  
 UMDW のデータ保持期間を構成できます。 詳細については、「[ユーティリティの管理 &#40;SQL Server Utility&#41;](../../database-engine/utility-administration-sql-server-utility.md)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のこのリリースで構成できない構成設定は次のとおりです。  
  
-   UMDW 名: Sysutility_mdw  
  
-   コレクション セットのアップロード頻度: 15 分ごと  
  
 UMDW ディレクトリ \<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\ (通常、\<System drive> は C:\ ドライブ) は構成可能です。 ログ ファイル Sysutility_mdw_\<GUID>_LOG は同じディレクトリにあります。  
  
> [!NOTE]  
>  UMDW (sysutility_mdw) ファイルの場所を変更するには、デタッチとアタッチを使用する方法と ALTER DATABASE を使用する方法があります。 ALTER DATABASE の使用をお勧めします。 詳細については、「[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server ユーティリティの機能とタスク](sql-server-utility-features-and-tasks.md)  
  
  
