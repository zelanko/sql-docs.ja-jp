---
title: 開発用データベース、テスト用データベース、および実行時用データベース | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- production databases [SQL Server]
- testing databases
- database testing [SQL Server]
ms.assetid: cb403330-8cbe-41c6-bd23-bc432d50f173
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 072f7d671f12335928984d4cebfe57f5bbfe6468
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="development-test-and-production-databases-visual-database-tools"></a>開発用データベース、テスト用データベース、および実行時用データベース (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
まったく同じ構成のデータベースが 2 つある場合は、一方のデータベースで変更を行い、その変更をもう一方のデータベースに反映させることができます。 たとえば、個人で使用する開発用データベースとグループ全体で使用するテスト用データベースがある場合は、開発用データベースを変更してから、その変更をテスト用データベースに反映させます。  
  
これを実現するには、すべての変更を開発用データベースでの単一のセッション内で実行し、セッションの変更スクリプトを作成して、そのスクリプトを後からテスト用データベースで実行します。  
  
## <a name="see-also"></a>参照  
[マルチユーザー環境 (Visual Database Tools)](../../ssms/visual-db-tools/multiuser-environments-visual-database-tools.md)  
  
