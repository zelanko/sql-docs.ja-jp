---
title: テーブル ステートメントの制限 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- CREATE TABLE statement limitations [ODBC]
- ODBC SQL grammar, CREATE TABLE statement limitations
ms.assetid: c5067855-20c9-456f-8d63-f375b4297f2e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a83acb061cf8192dff1c6adede349f49a0b0bbdb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280873"
---
# <a name="create-table-statement-limitations"></a>CREATE TABLE ステートメントの制限事項
Access、Excel、または Paradox ドライバを使用し、テキストまたはバイナリ列の長さが指定されていない (または 0 として指定されている) 場合、列の長さは 255 に設定されます。  
  
 dBASE ドライバーを使用し、テキストまたはバイナリ列の長さが指定されていない (または 0 として指定されている) 場合、列の長さは 254 に設定されます。  
  
 最大 255 列がサポートされています。  
  
 Microsoft Excel ドライバが MicrosoftExcel 5.0、7.0、または 97 のデータ ソースで使用されている場合、以前に削除されたワークシートと同じ名前のワークシートを作成することはできません。 Microsoft Excel ドライバを使用してバージョン 5.0、7.0、または 97 のワークシートにアクセスする場合、DROP TABLE ステートメントを使用するとワークシートは消去されますが、ワークシート名は削除されません。  
  
 Paradox ドライバを使用する場合、テーブルにインデックスを定義した後は列を追加できません。 CREATE TABLE ステートメントの引数リストの最初の列が索引を作成する場合、2 番目の列を引数リストに含めることはできません。
