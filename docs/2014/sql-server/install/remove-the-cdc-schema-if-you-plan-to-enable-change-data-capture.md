---
title: 変更データキャプチャを有効にする予定がある場合は、cdc スキーマを削除する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- cdc schema
- change data capture
ms.assetid: 6a84aa25-0f31-4be3-b2dd-4f249b8254ae
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: abdb33fa3d1ff022a65ed569f19d48bcf4468501
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059144"
---
# <a name="remove-the-cdc-schema-if-you-plan-to-enable-change-data-capture"></a>変更データ キャプチャを有効にする場合に cdc スキーマを削除する
  データベースには、既に cdc スキーマが含まれています。 アップグレード後に変更データ キャプチャを有効にする場合は、まずこの cdc スキーマを削除する必要があります。 データベースで変更データ キャプチャを有効にすると、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]によって、cdc という名前の新しいスキーマが作成されます。  
  
  
