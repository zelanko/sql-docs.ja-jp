---
title: ドライバーとデータソースについて |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC data source administrator [ODBC], concepts
ms.assetid: 2bb83ef1-4bbe-4be3-8c32-c4d1140aae1d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4e9b7229882b3b7f94e6b059e04c6496bde09641
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67938042"
---
# <a name="about-drivers-and-data-sources"></a>ドライバーとデータ ソースについて
*ドライバー*は、ODBC 要求を処理し、データをアプリケーションに返すコンポーネントです。 必要に応じて、ドライバーは、アプリケーションの要求を、データソースによって認識される形式に変更します。 コンピューターのドライバーを追加または削除するには、ドライバーのセットアッププログラムを使用する必要があります。  
  
 *データソース*は、ドライバーによってアクセスされるデータベースまたはファイルであり、データソース名 (DSN) によって識別されます。 システムからデータソースを追加、構成、および削除するには、ODBC データソースアドミニストレーターを使用します。 次の表では、使用できるデータソースの種類について説明します。  
  
|データ ソース|[説明]|  
|-----------------|-----------------|  
|User|ユーザー Dsn はコンピューターに対してローカルであり、現在のユーザーのみが使用できます。 これらは、HKEY_CURRENT_USER レジストリサブツリーに登録されます。|  
|システム|システム Dsn は、ユーザー専用ではなく、コンピューターに対してローカルです。 システムまたは特権を持つすべてのユーザーは、システム DSN を使用して設定されたデータソースを使用できます。 システム Dsn は HKEY_LOCAL_MACHINE レジストリサブツリーに登録されます。|  
|ファイル|ファイル Dsn はファイルベースのソースであり、同じドライバーがインストールされていて、データベースにアクセスできるすべてのユーザー間で共有できます。 これらのデータソースは、ユーザー専用である必要はなく、コンピューターに対してローカルにすることもできません。 ファイルデータソース名は、専用レジストリエントリによって識別されません。代わりに、拡張子が dsn のファイル名で識別されます。|  
  
 ユーザーデータソースとシステムデータソースは、コンピューターに対してローカルであるため、*総称してコンピューターデータソース*と呼ばれます。  
  
 これらの各データソースには、[ **ODBC データソースアドミニストレーター** ] ダイアログボックスのタブがあります。 使用できるデータ ソースの詳細については、「 [データ ソース](../../odbc/reference/data-sources.md)」を参照してください。
