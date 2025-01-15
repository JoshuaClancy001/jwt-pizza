# Learning notes

## JWT Pizza code study and debugging

As part of `Deliverable ⓵ Development deployment: JWT Pizza`, start up the application and debug through the code until you understand how it works. During the learning process fill out the following required pieces of information in order to demonstrate that you have successfully completed the deliverable.

| User activity                                       | Frontend component | Backend endpoints | Database SQL                                   |
| --------------------------------------------------- | ------------------ | ----------------- | ---------------------------------------------- |
| View home page                                      |     home.jsx       |  none             |    none                                        |
| Register new user<br/>(t@jwt.com, pw: test)         |  register.jsx      | [POST]/api/auth   |  INSERT INTO user (name, email, password) VALUES (?, ?, ?)<br/>INSERT INTO userRole (userId, role, objectId) VALUES (?, ?, ?) |
| Login new user<br/>(t@jwt.com, pw: test)            |  login.jsx         | [PUT]/api/auth    | SELECT * FROM user WHERE email=?<br> SELECT * FROM userRole WHERE userId=? |
| Order pizza                                         | payment.jsx        | [POST]/api/order  | INSERT INTO dinerOrder (dinerId, franchiseId, storeId, date) VALUES (?, ?, ?, now()) <br/> INSERT INTO orderItem (orderId, menuId, description, price) VALUES (?, ?, ?, ?)|
| Verify pizza                                        |   delivery.jsx     | [POST]/api/order/verify | none                   |
| View profile page                                   | dinerDashboard.jsx | [GET]/api/order   | SELECT id, franchiseId, storeId, date FROM dinerOrder WHERE dinerId=? LIMIT ${offset},${config.db.listPerPage}<br/> SELECT id, menuId, description, price FROM orderItem WHERE orderId=?                                     |
| View franchise<br/>(as diner)                       | franchiseDashboard.jsx | [GET]/api/franchise |  SELECT objectId FROM userRole WHERE role='franchisee' AND userId=?|
| Logout                                              | logout.jsx         |[DELETE]/api/auth  |  DELETE FROM auth WHERE token=?                |
| View About page                                     | about.jsx                  |   none                |                  none                              |
| View History page                                   |      history.jsx              |    none               |                none                                |
| Login as franchisee<br/>(f@jwt.com, pw: franchisee) |   login.jsx                 |    [PUT]/api/auth               | SELECT * FROM user WHERE email=?<br> SELECT * FROM userRole WHERE userId=?                                               |
| View franchise<br/>(as franchisee)                  |    franchiseDashboard.jsx                |  [GET]/api/franchise                 |  SELECT objectId FROM userRole WHERE role='franchisee' AND userId=? <br/> SELECT id, name FROM franchise WHERE id in (${franchiseIds.join(',')})                                             |
| Create a store                                      |  createStore.jsx                  |  [POST]/api/auth/franchiseid/store                 | SELECT u.id, u.name, u.email FROM userRole AS ur JOIN user AS u ON u.id=ur.userId WHERE ur.objectId=? AND ur.role='franchisee'                                               |
| Close a store                                       | closeStore.jsx                   | [DELETE]api/franchise/franchiseid/store/storeid                  |  SELECT u.id, u.name, u.email FROM userRole AS ur JOIN user AS u ON u.id=ur.userId WHERE ur.objectId=? AND ur.role='franchisee'<br/> DELETE FROM store WHERE franchiseId=? AND id=?                                              |
| Login as admin<br/>(a@jwt.com, pw: admin)           |                    |                   |                                                |
| View Admin page                                     |                    |                   |                                                |
| Create a franchise for t@jwt.com                    |                    |                   |                                                |
| Close the franchise for t@jwt.com                   |                    |                   |                                                |
