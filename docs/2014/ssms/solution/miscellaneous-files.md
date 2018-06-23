---
title: その他のファイル | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- files [SQL Server Management Studio], miscellaneous
- projects [SQL Server Management Studio], files
- solutions [SQL Server Management Studio], files
- miscellaneous files folder [SQL Server]
ms.assetid: 3c952b0b-8f5f-4d86-9e5d-616c10b9df0d
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e939419a42231a7885a2d957bca218725e19ae80
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077253"
---
# <a name="miscellaneous-files"></a>その他のファイル
  プロジェクトの外部のファイルのことを *その他のファイル*といいます。 ソリューションを開いているときには、プロジェクトに関連するその他のファイルを開いて修正できます。 その他のファイルとして分類されるのは、プロジェクトのコード エディターにファイル拡張子が関連付けられていないファイルです。 たとえば、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] スクリプト プロジェクトの場合、拡張子が .txt や .mdx のファイルはその他のファイルとして扱われます。 MDX プロジェクトでは、拡張子が .txt や .sql のファイルはその他のファイルとして扱われます。 ファイル拡張子をコード エディターに関連付けるを参照してください。[関連付けるファイル拡張子をコード エディターに](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md)です。  
  
 プロジェクトにその他のファイルを追加する機能は、いろいろな面で役立ちます。 たとえば、ソリューションの開発に不可欠ではあっても、必ずしもスクリプトとして認識されているわけではないファイルが存在します。 一般的な例としては、開発に関するメモや指示書、データ ファイル、コードの一部などがあります。  
  
 その他のファイルを活用すれば、柔軟な対応が可能になります。 たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] スクリプト プロジェクトに、テーブルやストアド プロシージャをデータベース内に作成するためのスクリプトがいくつかあるとします。 また、テーブルのデータ ファイルとして拡張子 .BCP のファイルがいくつかあり、実行用の指示書として README.TXT ファイルがあるとします。 そのようなデータ ファイルや README ファイルをその他のファイルとしてプロジェクトに追加すれば、プロジェクト システムのソース管理機能や他の機能を活用できるようになります。  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のメニューやツール バーは、開くファイルの形式に応じて変わるようになっています。 たとえば、テキスト ファイルを開けば、[テキスト エディター] ツール バーが表示されます。 XML スキーマ ファイルを開けば、[XML スキーマ] ツール バーが表示されます。 XML スキーマを編集しているときに、[テキスト エディター] ツール バーは使用できません。 プロジェクト ファイルからその他のファイルに切り替えれば、プロジェクトに関連したコマンドやツール バーがすべてその他のファイルに関連したコマンドやツール バーに置き換えられます。  
  
## <a name="see-also"></a>参照  
 [ソリューションとプロジェクトを管理するファイル](files-that-manage-solutions-and-projects.md)   
 [ソリューション&#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md)   
 [プロジェクト (SQL Server Management Studio)](projects-sql-server-management-studio.md)  
  
  