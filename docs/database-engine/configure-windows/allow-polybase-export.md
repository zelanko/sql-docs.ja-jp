---
title: allow polybase export の構成オプション | Microsoft Docs
description: SQL Server の設定で `allow polybase export` 構成オプションを設定する
ms.custom: ''
ms.date: 07/10/2020
ms.prod: sql
ms.prod_service: ''
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c25a7e42b55561ed6337281497e847999d722292
ms.sourcegitcommit: dacd9b6f90e6772a778a3235fb69412662572d02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2020
ms.locfileid: "86279651"
---
# <a name="set-allow-polybase-export-configuration-option"></a>`allow polybase export` 構成オプションの設定

[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

`allow polybase export` サーバー構成オプションを使用すると、Hadoop 外部テーブルに対して `INSERT` を実行できます。 

この機能は、他の外部データ ソースへの挿入をサポートしません。

 次の表に、このオプションで使用可能な値を示します。 

| 値 | 意味                                |
|-------|----------------------------------------|
| 0     | 無効。 これが既定の設定です。 |
| 1     | Enabled                                |


設定はすぐに有効になります。

## <a name="example"></a>例

次の例では、この設定を有効にします。

```sql
sp_configure 'show advanced options', 1;
GO
RECONFIGURE;
GO
sp_configure 'allow polybase export', 0;
GO
RECONFIGURE;
GO
```

## <a name="next-steps"></a>次のステップ

 [データのエクスポート](../../relational-databases/polybase/polybase-configure-hadoop.md#exporting-data)