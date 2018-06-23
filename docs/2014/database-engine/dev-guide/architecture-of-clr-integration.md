---
title: CLR 統合のアーキテクチャ |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], architecture
- architecture [CLR integration]
ms.assetid: 05e4b872-3d21-46de-b4d5-739b5f2a0cf9
caps.latest.revision: 39
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b408bcb655329c85bc39dea2c4ccfde68ac753db
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36082836"
---
# <a name="architecture-of-clr-integration"></a>CLR 統合のアーキテクチャ
  データベース プログラマは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と .NET Framework CLR (共通言語ランタイム) との統合により、Visual C#、Visual Basic .NET、Visual C++ などの言語を使用できます。 プログラマがこれらの言語を使用して記述できるビジネス ロジックには、関数、ストアド プロシージャ、トリガー、データ型、集計などがあります。  
  
 ここでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内部の CLR 統合アーキテクチャについて説明します。また、安全性、拡張性、効率性に優れ、セキュリティで保護されたユーザー コード実行環境が、このアーキテクチャによってどのように提供されるかについても説明します。  
  
 次の表は、このセクションのトピックを一覧表示します。  
  
 [CLR ホスト環境](../../relational-databases/clr-integration/clr-integration-architecture-clr-hosted-environment.md)  
 CLR 統合アーキテクチャの設計目標、メカニズム、および利点について説明します。  
  
 [CLR 統合のパフォーマンス](../../relational-databases/clr-integration/clr-integration-architecture-performance.md)  
 CLR 統合アーキテクチャのパフォーマンスに関する考慮事項について説明します。  
  
  