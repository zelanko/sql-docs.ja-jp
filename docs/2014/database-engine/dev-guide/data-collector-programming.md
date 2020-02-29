---
title: データコレクターのプログラミング |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- data collector [SQL Server], programming
ms.assetid: 53b4752b-055d-4716-b2bc-75b4cce84101
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 889158e04cbadb63c712ead73a61a7002ea61eae
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2020
ms.locfileid: "78175371"
---
# <a name="data-collector-programming"></a>データ コレクターのプログラミング
  
  <xref:Microsoft.SqlServer.Management.Collector> のデータ コレクター API を使用すると、オブジェクト モデルを通じてすべての構成操作をプログラムで制御できます。 また、API を使用するデータ収集操作の多くは、サーバーにインストールされているストアド プロシージャとして実装されます。

 次の図では、データ コレクター オブジェクト モデルの主要な要素を示します。

 ![データ コレクター オブジェクト モデル](../../../2014/database-engine/dev-guide/media/dc-objectmodel.gif "データ コレクター オブジェクト モデル")


