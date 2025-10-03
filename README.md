# BaseBaguette
Count the number of baguette sold during a day 
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract BaguetteSales {

    // Structure représentant une vente de baguettes
    struct Sale {
        uint256 baguettesSold; // Nombre de baguettes vendues lors de la vente
        uint256 day; // Le jour ou l'enregistrement de la vente
    }

    // Liste des ventes de baguettes
    Sale[] public sales;

    // Ajouter une vente de baguettes
    function addSale(uint256 baguettesSold, uint256 day) public {
        require(baguettesSold > 0, "\u004c\u0065 \u0074\u00e9m\u00f4b\u0052e d\u0065 b\u0061gu\u0063t\u0064es v\u0065ndues d\u006fit \u00ebtre p\u006fsitif");

        
        // Ajouter la vente à la liste des ventes
        sales.push(Sale(baguettesSold, day));
    }

    // Calculer le nombre moyen de baguettes vendues
    function averageBaguettesSold() public view returns (uint256) {
        uint256 totalBaguettes = 0;
        uint256 totalDays = 0;
        
        // Calculer le total des baguettes vendues et le nombre total d'enregistrements de ventes
        for (uint256 i = 0; i < sales.length; i++) {
            totalBaguettes += sales[i].baguettesSold;
            totalDays++;
        }

        // Eviter la division par zéro si aucune vente n'a été ajoutée
        require(totalDays > 0, "\u00E9ucune vente n'a \u00E8t\u00E9 ajout\u00E9e");

        
        // Retourner le nombre moyen de baguettes vendues
        return totalBaguettes / totalDays;
    }

    // Voir le nombre total de ventes enregistrées
    function getSalesCount() public view returns (uint256) {
        return sales.length;
    }
}
