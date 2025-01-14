# Learning notes

## JWT Pizza code study and debugging

As part of `Deliverable ⓵ Development deployment: JWT Pizza`, start up the application and debug through the code until you understand how it works. During the learning process fill out the following required pieces of information in order to demonstrate that you have successfully completed the deliverable.

| User activity                                       | Frontend component | Backend endpoints | Database SQL |
| --------------------------------------------------- | ------------------ | ----------------- | ------------ |
| View home page                                      |home.jsx            |  none             |  none        |
| Register new user<br/>(t@jwt.com, pw: test)         |login.jsx           |[PUT] /api/auth    |INSERT INTO user (name, email, password) VALUES (?, ?, ?)<br/> INSERT INTO userRole (userId, role, objectId) VALUES (?, ?, ?) |
| Login new user<br/>(t@jwt.com, pw: test)            |login.tsx           |/api/auth 'PUT'    |INSERT INTO user (name, email, password) VALUES (?, ?, ?)<br/> INSERT INTO userRole (userId, role, objectId) VALUES (?, ?, ?) |
| Order pizza                                         |menu.tsx, payment.tsx, delivery.tsx|'/api/order', 'POST'|INSERT INTO dinerOrder (dinerId, franchiseId, storeId, date) VALUES (?, ?, ?, now())INSERT INTO orderItem (orderId, menuId, description, price) VALUES (?, ?, ?, ?)|
| Verify pizza                                        |delivery.tsx        |/api/order/verify', 'POST'|none              |
| View profile page                                   |dinerDashboard.tsx  |/api/order         |SELECT id, franchiseId, storeId, date FROM dinerOrder WHERE dinerId=? LIMIT ${offset},${config.db.listPerPage}`, [user.id] SELECT id, menuId, description, price FROM orderItem WHERE orderId=?`, [order.id]              |
| View franchise<br/>(as diner)                       |franchiseDashboard.tsx| none            | none         |
| Logout                                              |logout.tsx          |'/api/auth', 'DELETE'|DELETE FROM auth WHERE token=?              | 
| View About page                                     |about.tsx           |none               |none              |
| View History page                                   |history.tsx         |none               |none              |
| Login as franchisee<br/>(f@jwt.com, pw: franchisee) |login.tsx           |/api/auth', 'PUT'  |INSERT INTO auth (token, userId) VALUES (?, ?) INSERT INTO userRole (userId, role, objectId) VALUES (?, ?, ?)              |
| View franchise<br/>(as franchisee)                  |franchiseDashboard.tsx|/api/franchise/${user.id}|`SELECT objectId FROM userRole WHERE role='franchisee' AND userId=?`, [userId]  `SELECT id, name FROM franchise WHERE id in (${franchiseIds.join(',')})`|
| Create a store                                      |                    |                   |              |
| Close a store                                       |                    |                   |              |
| Login as admin<br/>(a@jwt.com, pw: admin)           |                    |                   |              |
| View Admin page                                     |                    |                   |              |
| Create a franchise for t@jwt.com                    |                    |                   |              |
| Close the franchise for t@jwt.com                   |                    |                   |              |
