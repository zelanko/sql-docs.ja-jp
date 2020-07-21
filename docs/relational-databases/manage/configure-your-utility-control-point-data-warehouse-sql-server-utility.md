---
title: ユーティリティ コントロール ポイント データ ウェアハウスの構成 (SQL Server ユーティリティ) | Microsoft Docs
description: SQL Server のインスタンスにデータが格納されるユーティリティ管理データ ウェアハウスについて説明します。 データ保持期間およびディレクトリを構成する方法について説明します。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c2c6f050-8cdb-4b8e-ad38-4aae0a949847
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e35e6e779a138633c8ea15c79a2d1370c1b3edcf
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85775990"
---
# <a name="configure-your-utility-control-point-data-warehouse-sql-server-utility"></a>ユーティリティ コントロール ポイント データ ウェアハウスの構成 (SQL Server ユーティリティ)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージド インスタンスで収集されたデータは、ユーティリティ管理データ ウェアハウス (UMDW) に格納されます。UMDW ファイル名は sysutility_mdw です。  
  
 UMDW のデータ保持期間を構成できます。 詳細については、「[ユーティリティの管理 &#40;SQL Server ユーティリティ&#41;](https://msdn.microsoft.com/library/3e5a00c3-8905-40f0-9ddc-d924df9c2f0d)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のこのリリースで構成できない構成設定は次のとおりです。  
  
-   UMDW 名: Sysutility_mdw。  
  
-   コレクション セットのアップロードの頻度: 15 分ごと。  
  
 UMDW ディレクトリ \<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\ (通常、\<System drive> は C:\ ドライブ) は構成可能です。 ログ ファイル Sysutility_mdw_\<GUID>_LOG は同じディレクトリにあります。  
  
> [!NOTE]  
>  UMDW (sysutility_mdw) ファイルの場所を変更するには、デタッチとアタッチを使用する方法と ALTER DATABASE を使用する方法があります。 ALTER DATABASE の使用をお勧めします。 詳細については、「[ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server ユーティリティの機能とタスク](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
  
