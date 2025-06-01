    const buyerName = purchaseForm.buyerName.value.trim();
    const buyerEmail = purchaseForm.buyerEmail.value.trim();
    if (!buyerName || !buyerEmail) {
      alert('Por favor, preencha todos os campos.');
      return;
    }
    if (!selectedPack) {
      alert('Pacote não selecionado.');
      return;
    }
    // Simula confirmação de compra
    alert(`Compra confirmada!\n\nNome: ${buyerName}\nItem: ${selectedPack.title}\nValor: R$ ${selectedPack.price.toFixed(2)}`);
    // Salva no localStorage
    const purchaseData = {
      buyerName,
      buyerEmail,
      packId: selectedPack.id,
      packTitle: selectedPack.title,
      price: selectedPack.price,
      date: new Date().toLocaleString()
    };
    savePurchase(purchaseData);
    loadPurchases();
    closeModal();
  });
  closeModalBtn.addEventListener('click', closeModal);
  modalOverlay.addEventListener('click', (e) => {
    if (e.target === modalOverlay) closeModal();
  });
  // Inicializa a loja
  renderAllPacks();
  loadPurchases();
</script>
</body>
</html>
