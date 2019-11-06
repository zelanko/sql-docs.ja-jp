---
title: バックアップとハードウェアの Parallel Data Warehouse の読み込み
description: エンド ツー エンド データ ウェアハウス ソリューションでは、Analytics Platform System (APS) と並列データ ウェアハウス (PDW) をデプロイするには、データ ウェアハウスのバックアップを作成してデータを読み込むのための計画を作成する必要があります。 取得およびバックアップと読み込みビジネス要件を満たしているサーバーを構成するには、このガイダンスを使用します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 90f142a8bb86f99ed5cf5d9ff926bdf849060324
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961416"
---
# <a name="backup-and-loading-hardware-overview---parallel-data-warehouse"></a>バックアップとハードウェアの概要 - Parallel Data Warehouse の読み込み
エンド ツー エンド データ ウェアハウス ソリューションでは、Analytics Platform System (APS) と並列データ ウェアハウス (PDW) をデプロイするには、データ ウェアハウスのバックアップを作成してデータを読み込むのための計画を作成する必要があります。 取得およびバックアップと読み込みビジネス要件を満たしているサーバーを構成するには、このガイダンスを使用します。  
  
## <a name="acquire-and-configure-backup-servers"></a>取得し、バックアップ サーバーの構成  
![バックアップ プロセス](media/backup-process.png "バックアップ プロセス")  
  
PDW のデータベースをバックアップするには、バックアップ サーバーが 1 つまたは複数必要があります。 既存のハードウェアを使用して、または新しいハードウェアを購入することができます。 詳細については、次を参照してください。[の取得と Backup Server を構成](acquire-and-configure-backup-server.md)します。 この手順では、[バックアップ サーバー容量の計画ワークシート](backup-capacity-planning-worksheet.md)バックアップに最適なソリューションを計画します。  
  
## <a name="acquire-and-configure-loading-servers"></a>取得し、構成サーバーの読み込み  
![読み込みプロセス](media/loading-process.png "読み込みプロセス")  
  
データを読み込むには、1 つまたは複数のサーバーの読み込みする必要があります。 既存の ETL は、自分または他のサーバーを使用することができますか、新しいサーバーを購入することができます。 詳細については、次を参照してください。 [Acquire 読み込みサーバーの構成と](acquire-and-configure-loading-server.md)します。 この手順では、[サーバー容量の計画ワークシートの読み込み](loading-server-capacity-planning-worksheet.md)読み込みに最適なソリューションを計画します。  
  
## <a name="see-also"></a>関連項目  
[バックアップと復元の概要](backup-and-restore-overview.md)  
[負荷の概要](load-overview.md)  
  
