# Store

## CRUD OPERATIONS WITH QUERY
	@Modifying
	@Query(value = "INSERT INTO Products (name, price, quantity) VALUES (:name, :price, :quantity)", nativeQuery = true)
	@Transactional
	void insertProduct(@Param("name") String name, @Param("price") int price, @Param("quantity") int quantity);


	@Modifying
	@Query("UPDATE Products p SET p.name = :name, p.price = :price, p.quantity = :quantity WHERE p.id = :id")
	@Transactional
	void updateProduct(@Param("id") Long id, @Param("name") String name, @Param("price") int price, @Param("quantity") int quantity);

	@Modifying
	@Query("DELETE FROM Products p WHERE p.id = :id")
	@Transactional
	void deleteProduct(@Param("id") Long id);

	@Query("select b from Products b where b.name like %:name%")
	List<Products> SearchProductsByName(String name);
