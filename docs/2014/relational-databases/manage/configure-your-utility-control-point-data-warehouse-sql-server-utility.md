---
title: ユーティリティ コントロール ポイント データ ウェアハウスの構成 (SQL Server ユーティリティ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c2c6f050-8cdb-4b8e-ad38-4aae0a949847
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 60b9623b468f2763cf619c325412373e3603f3a3
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85023636"
---
# <a name="configure-your-utility-control-point-data-warehouse-sql-server-utility"></a>ユーティリティ コントロール ポイント データ ウェアハウスの構成 (SQL Server ユーティリティ)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージド インスタンスで収集されたデータは、ユーティリティ管理データ ウェアハウス (UMDW) に格納されます。UMDW ファイル名は sysutility_mdw です。  
  
 UMDW のデータ保持期間を構成できます。 詳細については、「[ユーティリティの管理 &#40;SQL Server ユーティリティ&#41;](../../database-engine/utility-administration-sql-server-utility.md)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のこのリリースで構成できない構成設定は次のとおりです。  
  
-   UMDW 名: Sysutility_mdw  
  
-   コレクション セットのアップロード頻度: 15 分ごと  
  
 UMDW ディレクトリは、MSSQL10_50 SQL Server 次のように構成 \<System drive> できます。: \mssql\data: <UCP_Name>。ここで、 \\ \<System drive> は通常は C:\ です。駆動. ログファイル Sysutility_mdw_ \<GUID> _LOG は、同じディレクトリにあります。  
  
> [!NOTE]  
>  UMDW (sysutility_mdw) ファイルの場所を変更するには、デタッチとアタッチを使用する方法と ALTER DATABASE を使用する方法があります。 ALTER DATABASE の使用をお勧めします。 詳細については、「[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server ユーティリティの機能とタスク](sql-server-utility-features-and-tasks.md)  
  
  
