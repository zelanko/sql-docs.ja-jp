---
title: 複数のアクティブな結果セット (MARS)
description: SqlDataReader の各インスタンスが個別のコマンドから起動された場合に、接続で複数の SqlDataReader を開く方法について説明します。
ms.date: 08/15/2019
ms.assetid: c90ef863-bac7-44cf-adc1-f05c36fcf57d
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 60c27bd94162b4d6bf4d7370218e1fa7781e6491
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75247695"
---
# <a name="multiple-active-result-sets-mars"></a>複数のアクティブな結果セット (MARS)

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET をダウンロードする](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

複数のアクティブな結果セット (MARS) は、複数のバッチを単一の接続で実行できるようにする機能です。 以前のバージョンでは、1 つの接続で一度に実行できるバッチは 1 つだけでした。 MARS を使用して複数のバッチを実行しても、これは必ずしも操作の同時実行を意味するわけではありません。  
  
## <a name="in-this-section"></a>このセクションの内容  
[複数のアクティブな結果セットの有効化](enable-multiple-active-result-sets.md)  
MARS を SQL Server で使用する方法について説明します。  
  
[データの操作](manipulate-data.md)  
MARS アプリケーションのコーディングの例を示します。  
  
## <a name="related-sections"></a>関連項目  
[非同期操作](asynchronous-operations.md)  
.NET の新しい非同期機能の使用方法について詳しく説明します。  
  
## <a name="next-steps"></a>次のステップ
- [SQL Server と ADO.NET](index.md)
