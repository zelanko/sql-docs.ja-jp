---
title: メタデータの保存 (OracleToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 9e49c25f-9216-43f4-8e99-2eaab298e215
author: nahk-ivanov
ms.author: alexiva
manager: alexiva
ms.openlocfilehash: d7287c5ed79834629c5cded6e29b87cf46d0e9ef
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87932853"
---
# <a name="save-metadata--oracletosql"></a>メタデータの保存 (OracleToSQL)
[**メタデータの保存**] ダイアログボックスでは、メタデータを保存する前に ssma プロジェクトに読み込むように求めるメッセージが表示されます。 これにより、オフラインで使用したり、技術サポート担当者などの他のユーザーに送信したりできる、完全なプロジェクトファイルを作成できます。  
  
[**メタデータの保存**] ダイアログボックスにアクセスするには、プロジェクトを保存します。 メタデータが見つからない場合は、SSMA によって [**メタデータの保存**] ダイアログボックスが表示されます。  
  
## <a name="options"></a>オプション  
**Name**  
プロジェクト内の各データベースの名前。  
  
**状態**  
メタデータが SSMA プロジェクトに読み込まれるかどうか、またはメタデータが存在しないかどうかを示します。  
  
SSMA は、必要に応じてメタデータをプロジェクトに読み込みます。 メタデータを参照し、スキーマを変換すると、メタデータが自動的に読み込まれます。  
  
**[すべて選択]**  
一覧表示されているすべてのデータベースを選択します。  
  
**[クリア]**  
メタデータが欠落しているすべてのデータベースのチェックボックスをオフにします。 メタデータが読み込まれている場合は、このチェックボックスをオフにすることはできません。  
  
**保存**  
プロジェクトを保存し、メタデータが存在しない選択したデータベースのメタデータを読み込みます。  
  
**キャンセル**  
保存操作をキャンセルします。 見つからないメタデータはプロジェクトに読み込まれません。  
  
