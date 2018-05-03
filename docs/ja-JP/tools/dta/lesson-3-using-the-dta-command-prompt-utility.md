---
title: 'レッスン 3: dta コマンド プロンプト ユーティリティを使用して |Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: dta
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-query-tuning
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- Database Engine [SQL Server], tutorials
ms.assetid: 30f27f4d-8852-4b12-ba62-57f63e496f1d
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 676d70c67a0be45b3362632c038d60e90448e90c
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="lesson-3-using-the-dta-command-prompt-utility"></a>レッスン 3 : dta コマンド プロンプト ユーティリティの使用
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] **dta** コマンド プロンプト ユーティリティでは、データベース エンジン チューニング アドバイザーで提供されるもの以外の機能も提供されます。  
  
データベース エンジン チューニング アドバイザーの XML スキーマを使用すれば、使い慣れた XML ツールで、このユーティリティへの入力ファイルを作成できます。 このスキーマは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール時にインストールされ、C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Binn\schemas\sqlserver\2004\07\dta\dtaschema.xsd に格納されます。  
  
データベース エンジン チューニング アドバイザーの XML スキーマは、 [Microsoft Web サイト](http://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409)から入手することもできます。  
  
この XML スキーマにより、チューニング オプションをより柔軟に設定することができます。 たとえば、"what-if" 分析を実行できます。 "what-if" 分析とは、チューニングするデータベースに対して実在の物理設計構造と仮想の物理設計構造のセットを指定し、それをデータベース エンジン チューニング アドバイザーで分析する手法です。これにより、仮想的な物理設計がクエリ処理のパフォーマンスを向上させるかどうかを判断できます。 このタイプの分析には、実際に実装しなくても新しい構成を評価できるという利点があります。 仮想的な物理構造により十分にパフォーマンスが向上しなくとも、十分な結果が得られる構成になるまで再び構造を変えて分析するのは容易です。  
  
また、データベース エンジン チューニング アドバイザーの XML スキーマと **dta** コマンド プロンプト ユーティリティを使用すると、データベース エンジン チューニング アドバイザーの機能をスクリプトに組み込み、そのスクリプトを他のデータベース設計ツールで使用することもできます。  
  
データベース エンジン チューニング アドバイザーの XML 入力機能の使用方法は、このレッスンでは扱いません。  
  
このレッスンでは、 **dta** コマンド プロンプト ユーティリティの基本的な構文を紹介するほか、ヘルプへのアクセス方法を説明し、簡単なワークロードをチューニングします。  
  
ここで説明する内容は次のとおりです。  
  
-   **dta** コマンド プロンプト ユーティリティの起動とワークロードのチューニング  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[dta コマンド プロンプト ユーティリティの起動とワークロードのチューニング](../../tools/dta/lesson-3-1-starting-the-dta-command-prompt-utility-and-tuning-a-workload.md)  
  
  
  
